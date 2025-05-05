# Aurora reproduce

For reproducing the results in "A Deep Reinforcement Learning Perspective on Internet Congestion Control".

## Project structure
- `aurora`: The git repo of aurora rl.
- `model_A`: The model trained from the default settings from the authors of the paper.
- `patch`: The patch used for port the aurora to ubuntu 24.04.
- `PCC-Uspace`: The git repo of PCC that handles receiving and sending packets - checkout the deep-learning branch before doing anything else!
- `scripts`: Scripts to be run in the vagrant vm - don't run them in host!


## Run the reproduce
Use
```shell
git submodule update --init --recursive
```
to init all submodule used.

Remember to checkout `deep-learning` branch of PCC-Uspace (The submodule should be automatically pointing to the correct commit. Verify it by checking the existence of the file `PCC-Uspace/Deep_Learning_Readme.md`).
```shell
# ./PCC-Uspace
git checkout deep-learning
```

Then, apply the patch for PCC-Uspace that ports it to python3.7:
```shell
# ./PCC-Uspace
git apply ../patch/pcc-uspace.patch
```

Now, start up the vm and refer to `scripts/train` and `scripts/test` for training the testing the model.
```shell
# ./
vagrant up
```