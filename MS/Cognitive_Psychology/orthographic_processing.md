## Orthographic Processing
![[ortho_processing.png]]
Orthographic processing is the interface between letters and words. It involves recognizing letters and their positions. In the 1970s, it was believed that somewhere in the brain, we have an array of ‘slots’ with a separate set of letter detectors for each slot.
![[ortho_processing_2.png|400]]
Word selectors are activated depending on which letter is activated most at each position. Activated words constraint letter detectors. This back-and-forth process repeats until word detector reaches a recognition threshold.
### Word Superiority Effect
![[word_superiority_text_img.png]]
James McKeen Cattell in 1886 found that letters in words are recognized faster than letters in non-words, a phenomenon known as the “word superiority effect”.
-> Letters are flexibly encoded for their positions

### Positional Noise and Bigram Representations
Potential solutions to positional encoding include positional noise where letters activate not only their slot but also surrounding slots,
![[pos_noice.png]]
and bigram representations where an intermediate layer between letters and words activates location-invariant letter combinations.
![[intermedaite_bigram.png]]
Recent research questions this theory. 
- Data can only be explained by a combination of absolute position coding and bigrams!
- Population receptive fields aren’t small enough to know single letter locations.
### PONG Theory
A new theory of orthographic processing is PONG (the Positional Ordering of N-Grams). The brain is a sequence learner and estimates the laterality of N-grams through bi-hemispheric activation differences.

![[pong.png]]