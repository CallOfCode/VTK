What is this project ?
----------------------

This project is **NOT** the official VTK repository.

It is a fork of VTK sources hosted at https://github.com/Kitware/VTK.

The official upstream repository is https://gitlab.kitware.com/vtk/vtk.

It is used as staging area to maintain and test patches that will be contributed back to the
official repository.


What is the branch naming convention ?
--------------------------------------

Each branch is named following the pattern `slicer-vY.Y.Z-YYYY-MM-DD-SHA{7}`

where:

* `vX.Y.Z` is the version of the forked project
* `YYYY-MM-DD` is the date of the last official commit associated with the branch.
* `SHA{7}` are the first seven characters of the last official commit associated with the branch.

For more details, see https://www.slicer.org/wiki/Documentation/Nightly/Developers/ProjectForks


How to update the version of VTK ?
----------------------------------

1. Clone this repository and add a remote to the official project

```
git clone git://github.com/Slicer/VTK
cd VTK
git remote add upstream git://github.com/kitware/VTK
git fetch upstream
```

2. Create a new branch following the convention

```
XYZ=X.Y.Z # Read it from https://github.com/Kitware/VTK/blob/master/CMake/vtkVersion.cmake

DATE=$(git show -s --format=%ci upstream/master | cut -d" " -f1)

SHA=$(git show -s --format=%h upstream/master)

git checkout -b slicer-v${XYZ}-${DATE}-${SHA} ${SHA}
```

3. Cherry-pick the Slicer specific commits from last branch. Resolve conflict as needed.

4. To **test the changes**, locally rebuild VTK, CTK and Slicer.

5. Publish the branch. (directly in this repo if you have push rights, or on a fork)

6. Update Slicer VTK external project and submit a pull request.


How to be granted push rights ?
-------------------------------

Ask on https://discourse.slicer.org/


Questions
---------

If you have questions, see https://discourse.slicer.org/
