# Neutron Emission Statistical Analysis

A Python-based analysis tool for characterizing neutron multiplication behavior in radioactive materials, developed during my internship at the **Bhabha Atomic Research Centre (BARC)**.

## Overview

This project implements statistical methods from *["The Idiot's Guide to the Statistical Theory of Fission Chains"](https://www.osti.gov/servlets/purl/966899)* (Lawrence Livermore National Laboratory) to analyze time-tagged neutron detection data and extract factorial moments used to characterize fission chain behavior.

The analysis takes raw pulse-timing data from a neutron detector, computes event counts across sliding time gates, and derives the factorial moments (Y1, Y2, Y3) and reduced factorial moments (Y2F, Y3F) that describe neutron multiplicity — a standard approach (the Feynman variance-to-mean method) for characterizing fissile material and reactor subcriticality.

## What it does

- **Loads and parses** raw list-mode digitizer data (board/channel/timetag/energy) from a CAEN-style detector output
- **Computes event counts** within sliding time gates across the dataset
- **Calculates statistical moments** (mean, variance, and higher-order moments) of the count distribution
- **Derives factorial moments** (Y1, Y2, Y3) and their reduced forms (Y2F, Y3F), following the LLNL statistical framework
- **Sweeps across gate widths** (1 ns to 512 ns) to study how these moments evolve with the measurement time window
- **Visualizes** the resulting count distributions and moment trends

## Tech stack

`Python` · `pandas` · `NumPy` · `SciPy` · `Matplotlib`

## Data

`DATAF__1.CSV` contains raw time-tagged detector events (~187,000 events) with columns for board, channel, timetag, energy, and energy-short — typical output format from a digital pulse-processing detector setup.

## Background

Factorial moment / Feynman variance-to-mean analysis is used in nuclear physics and safeguards applications to infer neutron multiplication characteristics of a sample from passive count-rate statistics, without needing an active interrogation source. This implementation was built to reproduce and explore that method on real detector data.

## Note

This was built as an internship project for internal analysis purposes; the underlying dataset is specific to the lab measurement it was collected from.
