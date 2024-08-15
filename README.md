# Distributed File System 

## Project Overview

This project implements a Distributed File System using socket programming. The system comprises three servers—`Smain`, `Spdf`, and `Stext`—and supports multiple client connections. Clients can upload, download, delete, and manage files through the `Smain` server, which coordinates with `Spdf` and `Stext` servers for handling `.pdf` and `.txt` files respectively.

## Features

- **Multiple Server Support**: The system consists of three servers:
  - `Smain`: Handles `.c` files locally and delegates `.pdf` and `.txt` files to other servers.
  - `Spdf`: Stores `.pdf` files.
  - `Stext`: Stores `.txt` files.
  
- **Client Commands**: The client can execute the following commands:
  - `ufile filename destination_path`: Uploads a file to `Smain` and delegates to the appropriate server if needed.
  - `dfile filename`: Downloads a file from `Smain` or the appropriate server.
  - `rmfile filename`: Deletes a file from `Smain` or the appropriate server.
  - `dtar filetype`: Creates and downloads a tar file containing all files of a specific type.
  - `display pathname`: Displays a list of all `.c`, `.pdf`, and `.txt` files in a directory.

## File Structure

- **Smain.c**: The main server code that handles `.c` files locally and coordinates with `Spdf` and `Stext` for `.pdf` and `.txt` files.
- **Spdf.c**: Server code dedicated to handling `.pdf` files.
- **Stext.c**: Server code dedicated to handling `.txt` files.
- **client24s.c**: Client-side code that allows users to interact with the distributed file system.

## Installation & Setup

1. Clone the repository to your local machine:
   ```sh
   git clone git@github.com:Shivam-Dogra/DistributedFileSystem.git
   ```

2. Compile each of the server and client programs:
   ```sh
   gcc Smain.c -o Smain
   gcc Spdf.c -o Spdf
   gcc Stext.c -o Stext
   gcc client24s.c -o client24s
   ```

3. Run the servers on different machines or terminals:
   ```sh
   ./Smain
   ./Spdf
   ./Stext
   ```

4. Run the client and execute commands:
   ```sh
   ./client24s
   ```

## Example Commands

- Upload a `.c` file:
  ```sh
  client24s$ ufile sample.c ~smain/folder1/folder2
  ```

- Download a `.pdf` file:
  ```sh
  client24s$ dfile ~smain/folder1/folder2/sample.pdf
  ```

- Remove a `.txt` file:
  ```sh
  client24s$ rmfile ~smain/folder1/folder2/sample.txt
  ```

- Create a tar file of all `.c` files:
  ```sh
  client24s$ dtar .c
  ```

- Display a list of all files in a directory:
  ```sh
  client24s$ display ~smain/folder1/folder2
  ```
