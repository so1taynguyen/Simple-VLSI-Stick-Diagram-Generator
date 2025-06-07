<a id="readme-top"></a>

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![Unlicense License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
	  <ul>
        <li><a href="#key-features">Key Features</a></li>
		<li><a href="#project-components">Project Components</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#how-to-run">How to run</a></li>
    <li><a href="#achievement">Achievement</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>

## About The Project

* This project is a C++-based Simple VLSI Stick Diagram Generator that creates CMOS stick diagrams from Boolean logic expressions. Using SFML for visualization, it constructs NMOS and PMOS transistor networks, supports series/parallel configurations, and optimizes layouts with Euler path computation.

<p align="right">(<a href="#readme-top">Back to top</a>)</p>

### Key Features

* Logic Parsing: Evaluates Boolean expressions (e.g., A+B, A*B) to build NMOS/PMOS networks.
* Graph Representation: Models transistor connections using graphs for series/parallel setups.
Euler Path: Optimizes transistor placement with Euler path computation.
* SFML Visualization: Displays color-coded stick diagrams (VDD, GND, Pdiff, Ndiff) with labels.
* Error Handling: Validates inputs, with console error messages.
* Modular Design: Separates expression evaluation (expr) and graph operations (graph).

<p align="right">(<a href="#readme-top">Back to top</a>)</p>

### Project Components

#### Source Files:

* [draw_stick_diagram.cpp](https://github.com/so1taynguyen/Simple-VLSI-Stick-Diagram-Generator/blob/main/src/draw_stick_diagram.cpp): Main program that handles user input, SFML window creation, and stick diagram rendering. It integrates logic element creation, edge extraction, and diagram drawing functions.
* [expression_euler_path.cpp](https://github.com/so1taynguyen/Simple-VLSI-Stick-Diagram-Generator/blob/main/src/expression_euler_path.cpp): Contains the core logic for parsing Boolean expressions, constructing NMOS/PMOS graphs, computing Euler paths, and filtering PMOS edges for accurate diagram generation.

<p align="right">(<a href="#readme-top">Back to top</a>)</p>

## Getting Started

To set up and run the Simple VLSI Stick Diagram Generator locally, install the required tools and follow the installation steps below.

### Prerequisites

The following tools are required to compile and run the project:

* **C++ Compiler**: A C++17-compatible compiler (e.g., g++, clang++). 
    * Example: MinGW
        * For 64-bit: https://github.com/brechtsanders/winlibs_mingw/releases/download/14.2.0posix-19.1.1-12.0.0-ucrt-r2/winlibs-x86_64-posix-seh-gcc-14.2.0-mingw-w64ucrt-12.0.0-r2.7z
        * For 32-bit: https://github.com/brechtsanders/winlibs_mingw/releases/download/14.2.0posix-19.1.1-12.0.0-ucrt-r2/winlibs-i686-posix-dwarf-gcc-14.2.0-mingw-w64ucrt-12.0.0-r2.7z
* **SFML**: Simple and Fast Multimedia Library for graphical rendering.
    * For 64-bit: https://www.sfml-dev.org/files/SFML-3.0.0-windows-gcc-14.2.0-mingw-64-bit.zip
    * For 32-bit: https://www.sfml-dev.org/files/SFML-3.0.0-windows-gcc-14.2.0-mingw-32-bit.zip

* **Chocolatey CLI**: For cmake installation. Open Powershell in adminstrator mode.
    ```powershell
    Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
    ```
    ```powershell
    choco upgrade chocolatey
    ```
* **CMake**: For building the project (optional, if using a CMake-based build system). Open Powershell in adminstrator mode.
    ```powershell
    choco install make
    ```
    * To verify: 
        ```powershell 
        make --version
        ```

### Installation

1. Clone the repository:

   ```sh
   git clone https://github.com/so1taynguyen/Simple-VLSI-Stick-Diagram-Generator.git
   cd Simple-VLSI-Stick-Diagram-Generator
   ```
2. Set correct path for MinGW & SFML to `Environment Variables` in control panel:

3. Change paths in the [Makefile](https://github.com/so1taynguyen/Simple-VLSI-Stick-Diagram-Generator/blob/main/src/Makefile) according to your own path to where you put SFML folder.
4. Compile the project (in Powershell):

   ```powershell
   make
   ```
5. Ensure the font file (`cambria_math.ttf`) is in the project directory or update the path in `draw_stick_diagram.cpp`.
6. Change the Git remote URL to avoid accidental pushes to the original repository:

   ```sh
   git remote set-url origin https://github.com/your_username/your_repo.git
   git remote -v # Confirm the changes
   ```

<p align="right">(<a href="#readme-top">Back to top</a>)</p>

## How to Run

Follow these steps to run the stick diagram generator:

1. Compile the project as described in the Installation section.
2. Run the executable (in Powershell):

   ```powershell
   .\draw_stick_diagram.exe
   ```
3. Enter a Boolean expression when prompted (e.g., `A+B*C`).
4. View the generated stick diagram in the SFML window.
   - **Components**: VDD (blue, top), GND (blue, bottom), Pdiff (brown), Ndiff (green), logic elements (red vertical lines), and connections (blue/red lines with black cross markers).
   - **Labels**: Logic elements, VDD, GND, and output (`Y`) are labeled.
5. Close the window or press `Escape` to exit.

**Example Input**:

```
Enter expression: (A+B)*C+D
```
![powershell](https://github.com/so1taynguyen/Simple-VLSI-Stick-Diagram-Generator/blob/main/images/powershell.png)

**Output**: A stick diagram showing NMOS and PMOS transistor networks for the expression, with series/parallel connections and labeled components.

![Result](https://github.com/so1taynguyen/Simple-VLSI-Stick-Diagram-Generator/blob/main/images/result.png)

<p align="right">(<a href="#readme-top">Back to top</a>)</p>

## Achievement

The project generates accurate CMOS stick diagrams for Boolean expressions with these highlights:

* Expression Support: Handles A+B, A*B, A+B*C, and complex expressions (100% for 3 variables, ~90% for 4, ~75% for 5). Only supports AND/OR; no duplicate variables.
* Graph Accuracy: Constructs and filters NMOS/PMOS graphs for valid Euler paths, verified via console.
* Visualization: Renders clear, color-coded diagrams (VDD, GND, Pdiff, Ndiff, logic elements) using SFML.
* Error Handling: Detects empty/missing inputs with console warnings and SFML fallback messages.

<p align="right">(<a href="#readme-top">Back to top</a>)</p>

## Contributing

Contributions are welcome to enhance the project. Suggestions include adding support for more complex expressions, optimizing Euler path algorithms, or improving visualization.

1. Fork the project.
2. Create a feature branch:

   ```sh
   git checkout -b feature/YourFeatureName
   ```
3. Commit your changes:

   ```sh
   git commit -m "Add YourFeatureName"
   ```
4. Push to the branch:

   ```sh
   git push origin feature/YourFeatureName
   ```
5. Open a pull request.

<p align="right">(<a href="#readme-top">Back to top</a>)</p>

<!-- CONTACT -->
## Contact

[![Instagram](https://img.shields.io/badge/Instagram-%23E4405F.svg?logo=Instagram&logoColor=white)](https://www.instagram.com/_2imlinkk/) [![LinkedIn](https://img.shields.io/badge/LinkedIn-%230077B5.svg?logo=linkedin&logoColor=white)](https://www.linkedin.com/in/linkk-isme/) [![email](https://img.shields.io/badge/Email-D14836?logo=gmail&logoColor=white)](mailto:nguyenvanlinh0702.1922@gmail.com) 

<p align="right">(<a href="#readme-top">Back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/othneildrew/Best-README-Template.svg?style=for-the-badge
[contributors-url]: https://github.com/so1taynguyen/Simple-VLSI-Stick-Diagram-Generator/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/so1taynguyen/Simple-VLSI-Stick-Diagram-Generator.svg?style=for-the-badge
[forks-url]: https://github.com/so1taynguyen/Simple-VLSI-Stick-Diagram-Generator/network/members
[stars-shield]: https://img.shields.io/github/stars/so1taynguyen/Simple-VLSI-Stick-Diagram-Generator.svg?style=for-the-badge
[stars-url]: https://github.com/so1taynguyen/Simple-VLSI-Stick-Diagram-Generator/stargazers
[issues-shield]: https://img.shields.io/github/issues/so1taynguyen/Simple-VLSI-Stick-Diagram-Generator.svg?style=for-the-badge
[issues-url]: https://github.com/so1taynguyen/Simple-VLSI-Stick-Diagram-Generator/issues
[license-shield]: https://img.shields.io/github/license/so1taynguyen/Simple-VLSI-Stick-Diagram-Generator.svg?style=for-the-badge
[license-url]: https://github.com/so1taynguyen/Simple-VLSI-Stick-Diagram-Generator/blob/main/LICENSE
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/linkk-isme/