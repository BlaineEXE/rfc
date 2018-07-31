Rook (Ceph) Storage Itegration Validation

| Field  | Value      |
|:-------|:-----------|
| Status | Draft      |
| Date   | 2018-07-31 |

## Introduction

The Rook project (https://rook.io) aims to orchestrate file, block, and object
storage on Kubernetes. Of note, Rook can orchestrate Ceph storage, which can
provide all 3 of these access types with one underlying storage technology.
We propose to include basic validation for Rook into the Kubic-Project's 
continuous integration environment.

### Problem description

This change is important for ensuring that Kubic-Project is able to host Rook
reliably.

### Proposed change

As part of Kubic-Project's CI suite, install Rook (Ceph) and perform some basic
high-level tests to verify that persistent block, file, and object storage
is made available by Rook.

## Detailed RFC

A general overview of steps toward validating Rook:
 1. Install a Rook (Ceph) cluster on Kubic-Project
 2. Create a persistent volume claim against Rook (Ceph) block storage, and
    test that the storage works for read and write and is persistent.
 3. Create a PVC against Rook (Ceph) file storage, and test that it works
    for read and write and is persistent.
 4. Create a PVC against Rook (Ceph) object storage, and test that it works
    for read and write and is persistent.
 5. Optional/for further discussion: Run Rook's test suites against the test
    Rook install.
    
Steps 2-5 are independent of each other, but all are dependent on 1.
    
Rook has good documentation regarding how to deploy a rook-ceph cluster on its
website (https://rook.io). Doc source is on GitHub (https://github.com/rook/rook).
Additionally, the requesting author (@BlaineEXE) can help with any of the aboe
steps.

### Proposed change (Detailed)

Currently Rook uses FlexVolumes to make storage available. The initial version(s)
of this feature should validate the integration between Rook and Kubic-Project's
FlexVolume support. At a yet undetermined time in the future, Rook will deprecate
the FlexVolume implementation in favor of a CSI driver. At that time, this feature
will need to be updated to validate this CSI-layer integration.

The steps outlined in the section above may likely represent incremental milestones
toward implementing this full feature, and it may be that there is a fair bit of
time between each individual implementation. Steps 1 and 2 above are fairly well
understood by @BlaineEXE.

*More changes to be proposed by CaaSP team members.*

### Dependencies

*Dependencies to be proposed by CaaSP team members.*

### Concerns and Unresolved Questions

*Concerns to be proposed by CaaSP team members.*

## Alternatives

Currently, no alternatives to this proposal have been identified. Discussion is 
welcome. 

## Revision History:

| Date       | Comment       | Author                  |
|:-----------|:--------------|:------------------------|
| 2018-07-31 | Initial Draft | Blaine Gardner          |
