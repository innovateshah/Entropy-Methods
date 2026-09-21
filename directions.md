#Research Directions

## 1. t-wise Independence Concentration for Submodular Functions

See: https://theory.stanford.edu/~jvondrak/data/submodular-chernoff.pdf
Will something like the above hold under just t-wise independence for large enough t? In this context, see https://arxiv.org/pdf/2608.04125 (up to the end of Sec. 3).

A possible route (via entropy method) would be proving an alteration to tensorization of entropy that only requires t-wise independence. For instance instead of fixing all but $X_i$ you iterate over all t-sized pairs and fix that. Alternatively we could think of t-wise independence as a map from some (less in quantity) truly independent r.v.'s to some n t-wise independent variables.


## 2. The concentration inequality for Lipschitz functions

Essentially see if the result from the following paper can be improved. https://web.math.princeton.edu/~nalon/PDFS/itcs251.pdf.
I believe referring to theorem 3 from the paper.
