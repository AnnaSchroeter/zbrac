# Building and Releasing 

* Update version numbers:
  * On `src/zbrac/zbrac/interface.py` change `"titletext = "zBrac X.X.X"`
  * On `src/zbrac/setup.py` change `version='X.X.X'`
  * On `installer/setup-pack.iss `change `#define MyAppVersion "X.X.X"`
    * change `OutputBaseFileName=zBrac-X-X-X-win32-setup`
  * On `zbrac/blob/master/setup_cxfreeze.py` change `version='X.X.X'`

* Creating executable with `cx_freeze`
  * Run `build_exe.cmd`. 
    * It uninstalls `zbrac` python package if it is installed already
  * Installs `zbrac` package from source ( `src/zbrac/`)
  * Runs `python setup_cxfreeze.py build` based on the file `build_origin.py` 
    * Executable files are generated `build/` which is not tracked by git

* Creating installer 
  * InnoSetup has to be installed on the system
  * Run `installer/setup-pack.iss` with InnoSetup
  * The installer will be generated in `/installer`

* Releasing on PyPi
  * Create package gzips by `python setup.py sdist bdist_wheel`
  * Upload by `twine upload dist/*` (twine needs to be installed)

* Release on github 
  * Upload exe file on github releases 

* Merge develop to master
  * `git checkout master`
  * `git merge develop --no-ff` TODO: Learn more about no-ff
  * `git tag "vX.X.X"`
