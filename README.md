CMGTools repository living within the CMGTools subsystem
git clone -o <name> -b <branch> <url> CMGTools/

CMG twiki: https://twiki.cern.ch/twiki/bin/viewauth/CMS/CMGToolsReleasesExperimental



## Instructions for developers

```sh
# setup CMSSW and the base git
cmsrel CMSSW_7_6_3 
cd CMSSW_7_6_3/src 
cmsenv
git cms-init

# add the central cmg-cmssw repository to get the Heppy 76X branch
git remote add cmg-central https://github.com/CERN-PH-CMG/cmg-cmssw.git  -f  -t heppy_76X

# configure the sparse checkout, and get the base heppy packages
cp /afs/cern.ch/user/c/cmgtools/public/sparse-checkout_76X_heppy .git/info/sparse-checkout
git checkout -b heppy_76X cmg-central/heppy_76X

# add your mirror, and push the 76X branch to it
git remote add origin git@github.com:YOUR_GITHUB_REPOSITORY/cmg-cmssw.git
git push -u origin heppy_76X

# now get the CMGTools subsystem from the cmgtools-lite repository
git clone -o cmg-central https://github.com/CERN-PH-CMG/cmgtools-lite.git -b 76X  CMGTools
cd CMGTools 

# add your fork, and push the 76X branch to it
git remote add origin  git@github.com:YOUR_GITHUB_REPOSITORYcmgtools-lite.git 
git push -u origin 76X

#compile
cd $CMSSW_BASE/src && scram b -j 8
```

## Instructions for physics users
Consult your local developer.
