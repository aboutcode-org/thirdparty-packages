# thirdparty-packages

A collection of various pre-built thirdparty packages with their corresponding source code

## Adding a pypi package

1. Start from a configured virtualenv in scancode-toolkit.

2. Use the script at `etc/scripts/fetch_thirdparty.py` in scancode-toolkit to:
   
   - Download wheels and source archives for a package.
   - Generate ABOUT and LICENSE files for these.
   - Check that these ABOUT files are valid.

   Example command:

   `python etc/scripts/fetch_thirdparty.py --wheels --sdists --spec sample-package --latest-version --dest foo/`

   You can also specify a version by pinning the requirements:

   `python etc/scripts/fetch_thirdparty.py --wheels --sdists --spec sample-package==1.0.0 --dest foo/`


3. Move the wheels and source-archives to the `pypi` folder of your local `thirdparty-packages` repository.

   `mv foo/* ../thirdparty-packages/pypi`

4. Use the script at `etc/scripts/gen_pypi_simple.py` to generate a PyPI simple index from a directory.

   `python etc/scripts/gen_pypi_simple.py ../thirdparty-packages/pypi/`