<div align="center">
  <h1>🚁 Emergency Drone Coordination System</h1>
  <p>A Client-Server architecture based multithreaded simulation for coordinating drones and rescuing survivors.</p>
</div>

<br/>

## 🎯 About the Project

This project is a multithreaded, real-time simulation system designed to manage the interaction between Unmanned Aerial Vehicles (drones) and individuals awaiting rescue (survivors). The system utilizes a robust **Client-Server architecture** communicating over **TCP Sockets**. The server acts as the central command, handling control and data updates, while individual drone clients update and transmit their real-time status.

## ✨ Key Features

- **2D Grid-Based Mapping:** Simulates environments using a coordinate-based grid mapped to pixels (e.g., `map.width * CELL_SIZE`), allowing for precise positioning.
- **Client-Server Architecture:** Real-time data exchange between the central control system (Server) and individual drones (Clients) via TCP sockets.
- **Hardware-Accelerated Rendering:** Uses the **SDL2** library (`SDL_RENDERER_ACCELERATED` | `SDL_RENDERER_PRESENTVSYNC`) for high framerates and fluid visual feedback.
- **Multithreading & Synchronization:** Highly optimized multithreading using `pthreads`. Employs fine-grained **Mutex Locks** (`pthread_mutex`) to ensure thread-safe operations on dynamic data structures without heavy performance bottlenecks.
- **Dynamic Data Structures:** Manages drones and survivors using Linked Lists, allowing seamless addition/removal of entities dynamically.
- **State-Based Visual Feedback:** Drones are color-coded based on their current operational status (`IDLE`, `ON_MISSION`, `DISCONNECTED`) for immediate visual tracking.

## 📂 Repository Structure

```text
├── headers/                 # Header files defining structures and function prototypes (e.g., drone.h, map.h)
├── sistemProje2/            # Project sub-modules and additional resources
├── tests/                   # Unit tests and test configurations
├── Makefile                 # Build instructions for compiling the project
├── server.c                 # Server application handling central coordination and socket connections
├── drone_client.c           # Client application representing an individual drone
├── controller.c / ai.c      # Core logic handling drone movement, AI decision-making, and routing
├── view.c / map.c           # SDL2 rendering logic and 2D grid map management
├── drone.c / survivor.c     # Entity definitions and state management
└── list.c / globals.c       # Linked list implementations and global state variables
```

## 🛠️ Technologies Used

- **Programming Language:** C
- **Graphics Library:** SDL2 (Simple DirectMedia Layer)
- **Concurrency:** POSIX Threads (pthreads), Mutexes
- **Networking:** TCP/IP Sockets
- **Build Tool:** Make

## 🚀 Installation & Setup

### Prerequisites
Ensure you have a C compiler (`gcc`), `make`, and the `SDL2` development libraries installed on your system.
For Debian/Ubuntu-based systems:
```bash
sudo apt-get update
sudo apt-get install build-essential libsdl2-dev
```

### Build Instructions
#### 1. **Clone the Repository:**
   ```bash
   git clone https://github.com/BahadirKarsli/Emergency-Drone-Coordination-System.git
   cd Emergency-Drone-Coordination-System
   ```

#### 2. **Compile the Project:**
   Use the provided Makefile to compile both the server and client executables.
   ```bash
   make
   ```

## 💻 Usage Instructions

The simulation requires running the server first, followed by one or multiple drone clients.

### 1. **Start the Server:**
   Launch the central coordination server. This will initialize the map, spawn survivors, and wait for drone connections.
   ```bash
   ./server
   ```

### 2. **Connect Drone Clients:**
   Open a new terminal window/tab and start a drone client. You can run multiple clients to simulate a swarm.
   ```bash
   ./drone_client
   ```

### 3. **Simulation Mechanics:**
   - The visual window will display the grid map.
   - Drones will automatically communicate with the server to find and travel towards survivors (`ON_MISSION`).
   - Observe the terminal output for real-time socket communication logs and mutex locking events.

## 🤝 Contributing

Contributions, bug reports, and feature enhancements are welcome. Feel free to open an **Issue** or submit a **Pull Request** to improve the simulation algorithms, add lock-free data structures, or enhance the SDL2 rendering logic.
