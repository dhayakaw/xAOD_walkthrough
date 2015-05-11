# xAOD_walkthrough
Analysis framework based on Base,2.1.30 with SUSYTools-00-05-00-26.

## Contents of the package ----
./MyAnalysis : analysis package for EventLoop.
./lsfoutput  : empty directory to store LSF outputs (only for login.icepp.jp).
./result     : empty directory to store results of each EventLoop process will be in this directory.
./share      : contains misc. files (e.g. install.sh, GRL.xml, XSDB.txt).
./analysis/  : analysis codes
  --mkBasicPlots : ROOT script to make distributions of Data/MC.

## Usage -----
kinit [your account]@CERN.CH #not necessary but recommended
./share/install.sh #setting up RootCore and installing all necessary packages

## Tips / example -----
$source rcSetup.sh
$rc find_packages
$rc compile
$testRun -D test -n 10
$source share/runOnLocal.sh [Dataset directory] [Signal selection]
$source share/runOnLSF.sh [Dataset directory] [Signal selection]
$python share/mkFileList.py [optionally target directory]
$source share/runOnLSFSplitDS.sh [Dataset directory] [Signal selection]
$source share/mergeRootFiles.sh [tag(e.g. h0001)]
$bkill -u [your account] -b 0 #kill all your jobs on LSF
$bjobs -l
$bjobs -u all
$bjobs -a
$bhosts
$bqueues
