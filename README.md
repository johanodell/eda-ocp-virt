#   GitOps OpenShift-Virtualization and Event Driven Ansible Demo

This is a demo created for a Red Hat Tech Update in Stockholm.
We (me and [@cldmnky](https://github.com/cldmnky)) wanted to show how 
to use modern tools and ways of working to deploy and configure 
virtual machines in OpenShift-Virtualization. You can see the workflow 
of the demo in the diagram below. 

![Alt text](eda-demo.png?raw=true "EDA Demo")

tl:dr
 
deploy VM with GitOps, postconfig VM with apps by eventdriven 
ansible in combination with labels. 

As a developer you can deploy a standard "dumb" VM into 
OpenShift-Virtualization by using git. To configure and 
add functionality/apps you need in the VM, you can trigger
Ansible playbooks by using an EDA event source which 
in this demo reacts when VMIs (VirtualMachineInstance) pops up 
in a specific namespace (as a result of a git push/merge). It will 
tell Ansible to execute a job.That job will be executed against 
all hosts in the group label_app_techupdate which will be created 
by the kubevirt_inventory_plugin. It is configured to create 
groups based on labels for example. 

Technologies used: 
* OpenShift-Virtualization
* OpenShift-GitOps (ArgoCD)
* Ansible Automation Platform Operator in OCP.