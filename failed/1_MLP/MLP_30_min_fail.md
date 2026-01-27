# **MLP_30_min_fail.md**

## **Summary**

* **Status:** Failed
* **Time Limit:** 30 minutes
* **Completed Time:** 30 minutes
* **Extra Work After Timer:** 60 minutes

---

## **What Worked Within Time**

* Implemented custom `LayerNorm`
* Implemented custom `LinearLayer`
* Designed the full MLP structure
* Connected all layers correctly
* Completed forward pass without errors

---

## **What Was Not Completed**

* Loss function
* Probability calculation from logits
* Training loop
* Converting `data.txt` into usable `x` and `y`

---

## **Root Cause Analysis**

1. **Dataset Construction Blocker**
   Spent too much time trying to convert raw text into training tensors.
   This created early confusion and stalled progress.

2. **Shape Reasoning Failure**
   Lost time understanding how to select the correct probability for each sample:
   `probs[batch_index, true_label]`.

3. **Time Pressure Freeze**
   About ~20 minutes were lost stuck on shapes + loss logic, without making progress.

---

## **Technical Factors**

* Softmax output shape not visualized early
* Needed a clearer step-by-step plan for:
  logits → probabilities → cross-entropy
* Delay in switching to a dummy dataset when real data became a bottleneck

---

## **How It Was Fixed After Timer**

* Drew the exact tensor shapes on paper
* Rebuilt the softmax and cross-entropy logic slowly
* Verified batch indexing for true-class probability extraction
* Used a dummy dataset to complete training and verify correctness

---

## **Key Learning**

* Always finalize the core architecture first
* Never waste time on dataset formatting during a speedrun
* Confirm tensor shapes early (forward pass → softmax → indexing)
* Probability indexing is simple once shapes are clear
* Forward and backward flow becomes easier once output is fixed as `(batch_size, num_classes)`

---

## **Plan for Next Attempt**

* Start with an empty notebook
* Use a small dummy dataset to avoid overhead
* Complete the entire pipeline in **under 20 minutes**
* Add shape checks at each critical step to avoid confusion

---

## **Notes**

* If layer dimensions are consistent, an MLP will always output:
  **`(num_examples, num_classes)`**
* Confirming shapes early prevents most downstream mistakes.