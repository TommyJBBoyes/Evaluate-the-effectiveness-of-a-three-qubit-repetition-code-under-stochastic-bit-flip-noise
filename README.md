# Evaluating a Three-Qubit Repetition Code Under Stochastic Bit-Flip Noise
Simulating a three-qubit quantum repetition code in Qiskit to evaluate logical bit-flip error rates under stochastic noise and compare results with theory.


## Overview

This project uses Python, Qiskit, and Qiskit Aer to investigate the effectiveness of a three-qubit quantum repetition code under stochastic bit-flip noise. By varying the physical error probability, the simulation estimates the logical error rate and compares the results with theoretical predictions.

## Research Question

How effectively does a three-qubit repetition code protect a logical bit as the probability of independent physical bit flips increases?

## Method

A logical bit is encoded across three data qubits: `|0⟩` becomes `|000⟩`, while `|1⟩` becomes `|111⟩`. Stochastic X errors are introduced independently on the data qubits. Two ancilla qubits measure the parity of pairs of data qubits, providing a syndrome that identifies a likely single-qubit error.

The measured data is then corrected in classical post-processing and decoded using majority voting. The logical error rate is calculated as the proportion of simulation shots in which the decoded bit differs from the original input.

## Theoretical Model

For independent bit-flip errors with probability \(p\), ideal encoding and syndrome extraction, the theoretical logical error probability is

\[
P_L=3p^2(1-p)+p^3=3p^2-2p^3.
\]

This expression represents the probability that at least two of the three physical qubits flip. The simulation is compared against this prediction and against the error probability of an unencoded bit.

## Data Analysis

The experiment tests several physical error probabilities. For each setting, the code runs 100,000 shots, calculates the simulated logical error rate, evaluates the theoretical prediction, and plots both results for comparison.

The aim is to determine whether the repetition code reduces logical bit errors and how its effectiveness changes as physical noise increases.

## Limitations

The model assumes independent bit-flip errors and ideal encoding, syndrome extraction, and measurement. Error correction is performed on measured classical bits in post-processing rather than through real-time quantum correction gates. The experiment therefore evaluates classical bit preservation in the computational basis, not the preservation of arbitrary quantum superpositions.
