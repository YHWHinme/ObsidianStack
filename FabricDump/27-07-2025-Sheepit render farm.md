# Sheepit: A Free, Community-Driven Render Farm for Blender

This video explores Sheepit, a free distributed render farm specifically designed for Blender users.  It details how Sheepit works, its advantages and limitations, and whether it's the right choice for your projects.

## Sheepit's History and Growth [00:00:00-00:01:30]

*   **Origins:** Sheepit began in 2007 as a personal project by Lauren Cloe (Clu) to speed up his Blender renders.  [00:00:20]
*   **Early Growth:**  Partnering with Pier Allar, Sheepit launched publicly in 2008 and rapidly gained popularity within the Blender community. [00:00:40]
*   **Milestones:**  Significant growth is highlighted, showcasing a dramatic increase in rendered frames over the years (1 million by 2014, 10 million by 2016, 40 million by 2017, and over 460 million by mid-2025). [00:01:00]  This growth necessitated infrastructure upgrades and community fundraising. [00:01:15]
*   **Open Source:** Both the client (2014) and server (2025) code were eventually open-sourced. [00:01:20]


## How Sheepit Works [00:01:30-00:03:00]

*   **Distributed Rendering:** Sheepit utilizes a distributed rendering system powered by volunteer computers worldwide. [00:01:35]
*   **Job Submission:** Users upload their Blender projects to the Sheepit website, where the job is split into tasks (per frame or tile). [00:02:00]
*   **Volunteer Contribution:** Volunteers run the Sheepit client on their machines, contributing their CPU and GPU power.  No Blender installation is required on the volunteer's machine; the necessary version is downloaded automatically. [00:02:20]
*   **Process:**  The client requests work, renders assigned tasks, and uploads the results back to the server.  The server manages task allocation based on machine capabilities. [00:02:40]
*   **Security:**  The system prevents direct communication between volunteer machines, ensuring security and reliability. [00:02:50]


## Job Submission and Monitoring [00:03:00-00:03:45]

*   **Web Interface:** Users manage projects via a web interface, specifying parameters like Blender version, frame range, render type (CPU, GPU, or both), and splitting options for high-resolution stills. [00:03:05]
*   **Queue and Prioritization:** Projects are added to a global queue and processed based on a point-based credit system. [00:03:20]
*   **Live Monitoring:** Users can monitor the rendering progress, preview outputs, and restart problematic frames. [00:03:30]
*   **Project Purging:**  Sheepit automatically deletes projects after 9 days; users should download their renders promptly. [00:03:40]


## The Sheepit Credit System [00:03:45-00:04:30]

*   **Points-Based System:**  A point system incentivizes contribution. Rendering for others earns points; using the farm spends points. [00:03:50]
*   **Priority Queue:**  More points mean higher priority in the render queue.  New users and slower machines receive special handling. [00:04:05]
*   **Balance:** The system balances rendering and consumption, encouraging active contribution.  Users who only submit jobs without volunteering will face delays. [00:04:20]


## Limitations of Sheepit [00:04:30-00:05:30]

*   **No Guaranteed Speed:** Rendering speed and wait times are not guaranteed due to reliance on volunteer resources.  Queue delays are possible, especially for low-priority projects or during peak usage. [00:04:35]
*   **Unsuitable for Sensitive Projects:**  The distributed nature of the system makes it unsuitable for proprietary, confidential, or client-sensitive projects due to potential data exposure.  Thumbnails of rendered frames are publicly visible. [00:04:55]
*   **Project Size Limits:**  There are limitations on project size, potentially requiring optimization (e.g., texture compression) for very large scenes. [00:05:20]


## Conclusion [00:05:30-00:05:45]

Sheepit offers a valuable free rendering solution for Blender users, but its reliance on volunteer resources and limitations regarding sensitive projects should be carefully considered.  It's ideal for personal or open-source projects but not recommended for commercial work requiring strict deadlines or data confidentiality.
