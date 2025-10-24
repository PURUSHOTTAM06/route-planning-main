High-Performance Route Planning Engine

This guide provides the necessary instructions for compiling and running the Route Planning Engine specifically on a Windows environment, prioritizing the use of Windows Subsystem for Linux (WSL) for a stable C++ development experience.

💻 Core Technologies

Primary Language: C++ (using modern standards)

Compilation: CMake

Build System: Make (GNU Make)

Operating System Focus: Windows Subsystem for Linux (WSL/Ubuntu)

Visualization: io2d Graphics Library (Submodule)

Data Source: OpenStreetMap (OSM) data structure

Project Setup (Cloning & Initialization)

This project relies on a critical graphics submodule for visualization. To ensure all dependencies are correctly initialized upon cloning, you must use the --recurse-submodules flag:

Using HTTPS (Recommended):

git clone <YOUR_PROJECT_NAME> --recurse-submodules



Using SSH:

git clone <YOUR_PROJECT_NAME_SSH> --recurse-submodules



Dependencies for Running Locally (Windows via WSL)

We highly recommend using the Windows Subsystem for Linux (WSL) with a distribution like Ubuntu for reliable compilation of C++ projects and the required graphics library.

Dependency

Installation Method (Inside WSL/Ubuntu)

cmake >= 3.11.3

sudo apt install cmake

make >= 4.1

Installed by default with build-essential.

gcc/g++ >= 7.4.0

sudo apt install build-essential

Graphics Library (io2d)

Follow the detailed installation steps below.

Graphics Library Installation (io2d via WSL/Ubuntu)

This project requires the io2d graphics implementation, which is included as a submodule in the project folder (P0267_RefImpl). You must compile and install it first.

Update and Install Core System Dependencies:

sudo apt update
sudo apt install build-essential cmake libcairo2-dev libgraphicsmagick1-dev libpng-dev



Initialize and Build the Graphics Submodule:

Navigate to the submodule's directory, build, and install its required files:

cd P0267_RefImpl
mkdir Debug
cd Debug
cmake ..
cmake --build .
sudo make install



Note: If you see an error about git clone, run git submodule update --init --recursive from the project root directory and repeat the steps above.

Compiling and Running the Engine

All compilation and running steps should be performed inside your WSL terminal.

Compiling

Create a build directory and navigate into it from the project root:

mkdir build && cd build



Run cmake and make to compile the core engine:

cmake ..
make



Running

The executable will be placed in the build directory.

Run the engine with the default map data:

./OSM_A_star_search



To specify a custom map file:

./OSM_A_star_search -f ../<your_osm_file.osm>



Testing

The unit testing executable is also placed in the build directory. From within build, you can run the unit tests as follows:

./test



Troubleshooting

Windows Specific Guidance

If you encounter issues during the IO2D installation or compilation process:

Verify WSL Configuration: Ensure the Windows Subsystem for Linux (WSL) is correctly enabled and that you are using a clean distribution like Ubuntu (available from the windows store).

Toolchain Alignment: Use the WSL toolchain within your IDE (like VS Code or CLion) to build the project, ensuring consistency between the compiler environment and the installed dependencies.

Dependency Issues

If cmake fails to find the installed graphics library (io2d packages), ensure you have correctly run sudo make install inside the P0267_RefImpl/Debug directory to place the necessary files in the WSL system paths.
