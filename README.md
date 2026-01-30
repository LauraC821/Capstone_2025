# Capstone_2025

## Project Overview

The capstone project is a **black box optimisation challenge** with the aim of identifying the maximum of 8 unknown functions. The project is reflective of real world bayesian optimisation problems, balancing exploration with exploitation to find global maxima with only limited queries of the true functions. 

### Inputs and Outputs
There are eight unknown functions of varying dimensionality, 2D-8D.
Each function has input variables in the range (0,1), with up to 6 decimal places.

A valid 3D function input has the form form, [0.240001, 0.873317, 0.555556].

Each function returns a single real valued output, for example 2.7963. 

## Objectives

The goal is to maximise each of the eight functions working within the following constraints:

The function structures are largely unknown.
There are only 13 opportunities to query the black box functions beyond the initial data.
