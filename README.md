# VVV

## Steps for setup:

1. release CMSSW_10_6_27
2. Set up NanoAOD tools
   ```bash
   cd $CMSSW_BASE/src

   git clone https://github.com/cms-nanoAOD/nanoAOD-tools.git PhysicsTools/NanoAODTools

   cd PhysicsTools/NanoAODTools

   cmsenv

   scram b
   ```

3. Set up VVV codes
   ```bash
   cd python/postprocessing

   ##clone this repository

   git clone https://github.com/gqlcms/XWWNano.git analysis

   cd $CMSSW_BASE/src

   scram b
   ```
    Noticed that the `crab_help.py` is written in python3, hence the `scram b` in CMSSW would leave some error message. Since this crab helper normally would not be included by other codes, you can ignore these errors.

4. Substitute some outdated files with `init.sh`
(refer to Meng's code: https://github.com/menglu21/TTC)
   ```bash
   cd $CMSSW_BASE/src/PhysicsTools/NanoAODTools/python/postprocessing/analysis

   source init.sh
   ```

## test

cd analysis/test
source run.sh
## crab

## <span id="Crab-mode"> Crab mode </span>
Crab mode is designed for data/MC.

```bash
cd crab
```
The crab mode is based on official nanotools. See reference: <https://github.com/cms-nanoAOD/nanoAOD-tools/tree/master/crab>

The `crab_help.py` is designed to simplify the repeated process. And the `input.json` is a sample for how to provide input for `crab_help.py`. `HWW_crab_script.sh` is the executed code on crab. 

First you need to generate the cfg file for crab job.
```bash
python3 crab_help.py -f input.json -m prepare
```
It will create a folder that with cfg files inside automatically. Noticed that some paths in `crab_help.py` need to be changed according to different user.

Then you can submit crab jobs with:
```bash
python3 crab_help.py -f input.json -m submit
```
Similarly, you can use `-m status`, `-m resubmit`, `-m kill` to batchly operate crab jobs.
(refer to Sen's code: https://github.com/Senphy/nanoAOD-WVG)
