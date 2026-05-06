# sleap-vame-behavior
# Pose Estimation and Unsupervised Behavioral Analysis Pipeline for Swimming Crab

This repository contains the analysis workflow used for pose estimation and unsupervised behavioral segmentation of the swimming crab (*Portunus trituberculatus*) under different environmental enrichment conditions. The pipeline integrates SLEAP-based pose estimation with VAME-based unsupervised behavioral analysis to extract behavioral motifs, quantify motif usage, and characterize behavioral transition dynamics.

## Overview

The workflow consists of two main steps:

1. **Pose estimation using SLEAP**
2. **Unsupervised behavioral segmentation using VAME**

SLEAP employs a convolutional neural network architecture to estimate animal body keypoints from video frames. Through supervised learning based on manually annotated images, SLEAP learns the mapping between raw video frames and keypoint probability heatmaps. Keypoint coordinates are then extracted from these heatmaps using peak detection, and predefined skeletal connections are used to reconstruct the spatial topology of crab body parts. This enables the generation of stable and high-resolution pose trajectories.

VAME uses the keypoint trajectories obtained from SLEAP as input. It extracts temporal kinematic features through a temporal encoding network and maps them into a continuous latent space. A decoder reconstructs the original pose sequences from the latent representation, ensuring that the latent embedding preserves behavioral dynamic information. Based on this latent space, VAME further applies Gaussian Mixture Models and Hidden Markov Models to discretize continuous behavioral dynamics into behavioral motifs, allowing the analysis of motif usage and behavioral sequence structure.
