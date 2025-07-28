# Goal: Activate Nix Flakes (Unspecified Time)

> At the time of this tutorial (July 2022), Nix Flakes are still an experimental feature and require some extra configuration to activate.

## Step 1: Add the `experimental-features` line to your Nix configuration.

This step enables Nix Flakes support. Choose one of the following options based on your system's configuration:

```bash
echo 'experimental-features = nix-command flakes' >> /etc/nix/nix.conf  # For system-wide configuration
```

or

```bash
echo 'experimental-features = nix-command flakes' >> ~/.config/nix/nix.conf  # For user-specific configuration
```

## Step 2: Verify Flakes Activation

After adding the line, verify that Nix Flakes are enabled:

```bash
nix flake --version
```

This command should output the Nix Flakes version.


# Goal: Create a New Nix Flake Project (Unspecified Time)

> Nix Flakes provide a convenient template system that makes starting new projects much easier. There exist default templates, and users can also define their own.

## Step 1: Choose a Template

Use `nix flake show templates` to list available templates.  The tutorial uses the `trivial` template.

```bash
nix flake show templates
```

## Step 2: Initialize the Flake

Use the `nix flake init` command to create a new flake project from a template.  The `-t` flag specifies the template. The tutorial demonstrates several ways to do this:

```bash
nix flake init -t templates#trivial  # Uses the trivial template
```

or

```bash
nix flake init -t templates # Uses the default template (which is trivial)
```

or even just:

```bash
nix flake init # Uses the default template (which is trivial)
```

This creates a `flake.nix` file in the current directory.


## Step 3: Initialize Git Repository

Nix Flakes require a Git repository. Initialize one in your project directory:

```bash
git init && git add flake.nix && git commit -m "Initial commit"
```

# Goal: Build and Run a Package within the Flake (Unspecified Time)

> This flake contains one package available for the `x86_64-linux` targets: the `hello` package.

## Step 1: Build the Package

Build the `hello` package using:

```bash
nix build .#hello
```

This command builds the package defined in the `flake.nix` file and places the result in a `result` directory.

## Step 2: Run the Package

Execute the built package:

```bash
./result/bin/hello
```

or using `nix run`:

```bash
nix run .#hello
```

Both commands should print "Hello, world!".


# Goal: Add an Input to the Flake (Unspecified Time)

> Let us add an input to the flake. We will add a specific version of `nixpkgs`.

## Step 1: Modify `flake.nix`

Add an `inputs` section to your `flake.nix` file, specifying the desired version of `nixpkgs`:

```nix
{
  description = "A very basic flake";

  inputs = {
    nixpkgs.url = "github:nixos/nixpkgs/22.05";
  };

  outputs = { self, nixpkgs }: {
    packages.x86_64-linux.hello = nixpkgs.legacyPackages.x86_64-linux.hello;
    defaultPackage.x86_64-linux = self.packages.x86_64-linux.hello;
  };
}
```

## Step 2: Update the Lock File

The `flake.lock` file needs to be updated to reflect the new input:

```bash
nix flake lock
```

This will download the specified version of `nixpkgs` and update the lock file.


# Goal: Update Inputs in the Flake (Unspecified Time)

> To update the version of **all** the inputs, run `nix flake update`. In the case where you only want to update a single input, use `nix flake lock --update-input <INPUT_NAME>`. For the `nixpkgs` input, this will be `nix flake lock --update-input nixpkgs`.


## Step 1: Update All Inputs

To update all inputs to their latest versions:

```bash
nix flake update
```

## Step 2: Update a Specific Input

To update only the `nixpkgs` input:

```bash
nix flake lock --update-input nixpkgs
```


# Goal: Define Custom Outputs in the Flake (Unspecified Time)

> Let us add our packages defining previously.

This section involves creating and adding custom packages to the flake.  The provided transcript details the `flake.nix` configuration, but lacks explicit step-by-step instructions for creating the packages themselves (which would reside in separate `pkgs` directories).  The steps below outline the flake configuration, assuming the packages are already created.

## Step 1: Modify `flake.nix`

Modify your `flake.nix` to include the custom packages. This example assumes packages are located in `./pkgs/chord` and `./pkgs/simgrid`:

```nix
{
  description = "A very basic flake";

  inputs = {
    nixpkgs.url = "github:nixos/nixpkgs/22.05";
  };

  outputs = { self, nixpkgs }:
    let
      system = "x86_64-linux";
      pkgs = import nixpkgs { inherit system; };
    in {
      packages.${system} = rec {
        chord = pkgs.callPackage ./pkgs/chord {};
        chord_custom_sg = pkgs.callPackage ./pkgs/chord { simgrid = custom_simgrid; };
        custom_simgrid = pkgs.callPackage ./pkgs/simgrid/custom.nix {};
      };
    };
}
```

## Step 2: Build and Test the Custom Packages

The instructions for building and testing the custom packages (`chord`, `chord_custom_sg`, `custom_simgrid`) are not explicitly detailed in the transcript.  This would involve building each package individually using Nix commands, depending on their individual build instructions.


# Goal: Add Backwards Compatibility with Older Nix (Unspecified Time)

> As Nix Flakes are still an experimental feature (at the time of this tutorial), you may want to provide a way for the users to interact with a flake via the classical nix CLI (i.e., `nix-build`, `nix-shell`, …).

## Step 1: Add `default.nix`

Create a `default.nix` file in the same directory as your `flake.nix` and `flake.lock`:

```nix
(import (
  fetchTarball {
    url = "https://github.com/edolstra/flake-compat/archive/12c64ca55c1014cdc1b16ed5a804aa8576601ff2.tar.gz";
    sha256 = "0jm6nzb83wa6ai17ly9fzpqc40wg1viib8klq8lby54agpl213w5";
  }
) {
  src =  ./.;
}).defaultNix
```

This allows interaction with the flake using the older Nix CLI.  Note that the attribute names will be the full output names (e.g., `packages.x86_64-linux.hello`).


# Goal: Add and Use a Custom Registry (Unspecified Time)

> You can add user-defined registries, which can be really helpful for end users.

## Step 1: Add the Registry

Add a custom registry using the `nix registry add` command.  The example uses a GitLab repository:

```bash
nix registry add mypkgs git+https://gitlab.inria.fr/qguillot/mypkgs_example
```

Replace the URL with your custom registry's location.

## Step 2: Use the Registry in a Flake

Reference the custom registry in the `inputs` section of another flake's `flake.nix` file:

```nix
{
  description = "My Experiments repo";

  inputs = {
    nixpkgs.url = "github:nixos/nixpkgs/22.05";
    mypkgs.url = "git+https://gitlab.inria.fr/qguillot/mypkgs_example";
  };

  # ... rest of the flake.nix ...
}
```

Then, use the packages from the custom registry in the `outputs` section, referencing them with the full path (e.g., `mypkgs.packages.${system}.chord`).


# Goal: Create a Development Shell using Packages from a Custom Registry (Unspecified Time)

> To use the packages, or other outputs, in another flake, we just need to add it to the `inputs` set.

This goal builds on the previous one, using packages from a custom registry to create a development shell.

## Step 1: Define the Development Shell in `flake.nix`

In your flake's `flake.nix`, define a `devShells` output that uses the packages from your custom registry:


```nix
outputs = { self, nixpkgs, mypkgs }:
  let
    system = "x86_64-linux";
    pkgs = import nixpkgs { inherit system; };
  in {
    devShells.${system} = {
      chordShell = pkgs.mkShell {
        buildInputs = [ mypkgs.packages.${system}.chord ];
      };
    };
  };
```

## Step 2: Enter the Development Shell

Enter the development shell using:

```bash
nix develop .#chordShell
```

This will create a shell environment with the `chord` package available.

