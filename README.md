# Plonk-DIZK GPU Acceleration

  

Prize Sponsor: Aleo

Prize Architect: Espresso Systems

## Prize Description

### Summary

Zero-knowledge cryptography can be parallelized through a technique known as DIZK. This prize will apply the DIZK approach for accelerating Plonk proof generation for gigantic circuits.

### Optimization Objective (1-sentence)

  

For a given set of clusters, minimize Plonk proof generation latency for gigantic circuits.

### Constraints

The only goal is to improve the proving time for a given circuit, in the form of plonk proving/verification keys. The circuit is defined below. Note that the competitors should not modify or optimize the circuit. The competitors should look into the internal proving functions and utilize multi-servers to accelerate the proving process.

  

The concrete proof system will be an instance of TurboPlonk in the Jellyfish crypto-library. Jellyfish will also contain a semi-optimized version of Rescue hash function over bls12-381::ScalarField. The submission may, and is encouraged to, alter the proof system in Jellyfish library, provided the correctness of the system (see correctness section).

  

The task is to optimize the Plonk prover, so essentially any dummy circuit can be used for evaluation. In the hope that the designed circuit may actually reflect a real world use case, we choose the following one. Note that this is only for reference purposes – we stress again that the actual design of the submission should be agnostic with regard to the actual circuit.

  

The circuit is designed with multiple membership proofs for merkle tree based accumulators, tentatively instantiated with the following parameters:

-   Use Rescue hash function with width = 4, over either bls12-381::ScalarField
    

-   Tree height set to 21
    
-   Number of membership proofs set to 2^16
    

  

The submission should not modify the above parameters. This design mimics the real world use case of zk-rollups.

  

Submissions must include documentation, in English, sufficient to explain the optimization approach

## Timeline

  

June 10 - Competition begins

September 10 - Mid-competition submission due

December 10 - Final submission due

---

## Judging

  

Submissions will be analyzed for both correctness and performance.

### Correctness

  

-   First, to enable competitors to test the correctness of their solutions before submitting, a set of test vectors will be provided at the start of the competition.
    
-   Competitors will be given a pair of testing proving key and verification key that helps validating testing vectors and testing.
    
-   The submission will provide an API that, up on some input Paths to merkle trees and the proving key, outputs a Plonk proof.
    
-   The inputs to the API for final competition, upon which a Plonk proof is generated, will be released after the submission. They will be generated via the same fashion as the testing proving key and verification key and Paths, but with a different PRNG seed.
    
-   The proof must pass the verification with the given verification key and public input.
    

### Performance

To evaluate the performance of each submission, the prize committee will sample tuples of inputs, proving keys, and verification keys. They are generated following the same fashion as the testing inputs/keys. The submitted score will be the *average* proof generation time for all instances.

  

In addition, all submissions will be manually reviewed by the prize committee.

### Hardware & Benchmarks

  

-   All submissions will be tested using a maximum of 6 servers, each equipped with 8 Intel Xeon v4 CPU cores, 100 GB of RAM, and an RTX 4000 GPU provided by Coreweave
    

  

---

## Prize Allocation

  

The prize amount will be divided among the top five finishers according to the following proportions:

  

-   If there are over 5 correct submissions, 60% to winning implementation, 20% to second place, and 10% to third place, 6% to the fourth place and 4% to the fifth place
    
-   If there are 4 correct submissions, 64% to winning implementation, 20% to second place, and 10% to third place, 6% to the fourth place
    
-   If there are 3 correct submissions, 70% to winning implementation, 20% to second place, and 10% to third place
    
-   If there are 2 correct submissions, 75% to winning implementation, 25% to second place
    
-   If there is only one correct submission, 100% to winning implementation
    

  

Prizes will be given out in good faith and in the sole discretion of the prize committee.

## Notes

  

All submission code must be open-sourced at the time of submission. Code and documentation must be dual-licensed under both the MIT and Apache-2.0 licenses

## Questions

  

If there are any questions about this prize, please contact zprize@espressosys.com

  

## References

  

[1] DIZK: A Distributed Zero Knowledge Proof System, Howard Wu, Wenting Zheng, Alessandro Chiesa, Raluca Ada Popa, and Ion Stoica, [https://www.usenix.org/conference/usenixsecurity18/presentation/wu](https://www.usenix.org/conference/usenixsecurity18/presentation/wu)
