<h1 align="center">
  <p align="center">admindojo.org</p>
  <a href="https://admindojo.org"><img height="300" src="https://admindojo.org/themes/admindojo/static/img/dojo_round.png" alt="admindojo"></a>
</h1>

# Develop trainings

## issue
Please create a issue for each training(idea) at: https://github.com/admindojo/admindojo-training/issues
Use the provided template - it contains a checklist to follow.

## naming
- each training needs a unique name - it's also refered as it's Training-ID
- naming convention: `<category>-<tool/subject>-<sub-subject>-<level|counter>-<OS or distribution>`

## template
To generate a training please use boilr - a template is available at: https://github.com/admindojo/boilr-templates.
The template generates all files necessary - other instructions may be out of date.
The files generated files include information how to customize them.

## shared configuration
`admindojo\` contains user files and common VM-configuration.
````text
admindojo\: is mounted to the traning VM -> \admindojo
admindojo\client:
admindojo\config: shared client configuration
admindojo\development: notes etc. used for development
admindojo\internal: Common configuration files
admindojo\internal\bootstrap.sh: Install required tools
admindojo\internal\destroy.sh: Cleanup at "vagrant destroy"
admindojo\internal\setup-dev-env.ps1:  Setup Dev-ENV for Windows 
admindojo\internal\setup-test-env.ps1:  Setup Test-ENV for Windows (auto test training)
admindojo\internal\teardown-test-env.ps1: Teardown Dev-ENV for Windows 
admindojo\internal\testing.sh: 
admindojo\internal\Vagrantfile-base: Common Vagrantfile
admindojo\results: User results. Client creates a directory named after a traning.
admindojo\results\$Trainingname: 
````

## training directory

````text
$trainingID\
$trainingID\README.md: Content that is used to generate the HTML page at admindojo.org. Should be usable without changes.
$trainingID\Vagrantfile: Base Vagrantfile
$trainingID\config\
$trainingID\config\Vagrantfile-overwrite-config: Overwrites for Vagrantfile
$trainingID\config\Vagrantfile-overwrite-vm: Overwrites for Vagrantfile
$trainingID\internal\
$trainingID\tmp\: Temporary files for training that should survive restart or reload. Removed at vagrant destroy
$trainingID\taining\: Inspec profile directory. Follows Inspec structure
$trainingID\taining\inspec.yaml: Content is used to generate the HTML page at admindojo.org
$trainingID\taining\token.sh: Script to generate a token for admindojo.org
$trainingID\taining\controls\: One test.rb that contains all tests for this training
$trainingID\taining\libraries\: See Inspec readme
$trainingID\taining\tests\: Scripts to fully test the training. Should contain everything to automatically succeed the training. 
````

## inspec verification/controls

## tests

Since admindojo is used to teach, each training should be 100% correct and solvable.
`$trainingID\taining\tests\` Should contain everything needed to solve the traning with 100%.
For simple tranings a bash script is ok.

To build VM, run tests and run Inspec:
1. `. admindojo\internal\setup-dev-env.ps1`
2. `. admindojo\internal\setup-test-env.ps1`
3. `vagrant up`
