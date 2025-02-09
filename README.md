# Dockerfile Bug: Missing Application File

This repository demonstrates a common error in Dockerfiles: attempting to run an application that hasn't been added to the image.  The provided `Dockerfile` attempts to execute a Python script (`/app/main.py`) but fails because the script isn't included in the image.

The solution demonstrates how to correctly copy the necessary application files into the image before attempting to run them.

## How to Reproduce

1. Clone this repository.
2. Build the image using the original `Dockerfile`:
   ```bash
   docker build -t faulty-app .
   ```
3. Attempt to run the container:
   ```bash
   docker run faulty-app
   ```
   This will result in an error because `/app/main.py` is not found.

4. Build the image using the corrected `Dockerfile_solution`:
   ```bash
   docker build -t fixed-app -f Dockerfile_solution .
   ```
5. Attempt to run the container:
   ```bash
   docker run fixed-app
   ```
   This will now work correctly.

## Files

- **Dockerfile**: The buggy Dockerfile.
- **Dockerfile_solution**: The corrected Dockerfile.
- **main.py**: A simple Python script to be executed in the container (added to the solution directory).