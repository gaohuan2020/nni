# Introduction 

NNI (Neural Network Intelligence) is a toolkit to help users running automated machine learning experiments. 
The tool dispatches and runs trial jobs that generated by tuning algorithms to search the best neural architecture and/or hyper-parameters at different environments (e.g. local, remote servers, Cloud).

```
            AutoML experiment                                 Training Services
┌────────┐        ┌────────────────────────┐                  ┌────────────────┐
│ nnictl │ ─────> │  nni_manager           │                  │ Local Machine  │
└────────┘        │    sdk/tuner           │                  └────────────────┘
                  │      hyperopt_tuner    │
                  │      evolution_tuner   │    trial jobs    ┌────────────────┐
                  │      ...               │     ────────>    │ Remote Servers │          
                  ├────────────────────────┤                  └────────────────┘
                  │  trial job source code │                  
                  │    sdk/annotation      │                  ┌────────────────┐
                  ├────────────────────────┤                  │ Yarn,K8s,      │
                  │  nni_board             │                  │ ...            │
                  └────────────────────────┘                  └────────────────┘
```
## **Who should consider using NNI**
* You want to try different AutoML algorithms for your training code (model) at local
* You want to run AutoML trial jobs in different environments to speed up search (e.g. remote servers, Cloud)
* As a researcher and data scientist, you want to implement your own AutoML algorithms and compare with other algorithms
* As a ML platform owner, you want to support AutoML in your platform

# Getting Started with NNI

## **Installation**
Install through python pip
* requirements: python >= 3.5
```
pip3 install -v --user git+https://github.com/Microsoft/nni.git
source ~/.bashrc
```


## **Quick start: run an experiment at local**
Requirements:
* with NNI installed on your machine.

Run the following command to create an experiment for [mnist]
```bash
    nnictl create --config ~/nni/examples/trials/mnist-annotation/config.yml
```
This command will start the experiment and WebUI. The WebUI endpoint will be shown in the output of this command (for example, `http://localhost:8080`). Open this URL using your browsers. You can analyze your experiment through WebUI, or open trials' tensorboard. Please refer to [here](docs/GetStarted.md) for the GetStarted tutorial.


# Contribute
NNI is designed as an automatic searching framework with high extensibility. NNI has a very clear modular design. Contributing more tuner/assessor algorithms, training services, SDKs are really welcome. Please refer to [here](docs/ToContribute.md) for how to contribute.

# Privacy Statement
The [Microsoft Enterprise and Developer Privacy Statement](https://privacy.microsoft.com/en-us/privacystatement) describes the privacy statement of this software.
