# Horizon Finding in Images

#### This was implemented under the valuable guidance of Prof David Crandall at Indiana University in B551 Elements of AI during Fall 2019.

A classic problem in computer vision is to identify where on Earth a photo was taken using visual features alone. For some images, this is relatively easy | a photo with the Eifiel tower in it was probably taken in Paris. One way of trying to geolocate such photos is by extracting the horizon (the boundary between the sky and the mountains) and using this as a \ngerprint" that can be matched with a digital elevation map to identify where the photo was taken.

### Part - I
In this part, we were supposed to build a Bayes net. So we used the edge map to and took the pixel with the highest transition-edge along each row for all the columns.

## Part - II
Since Bayes net relies only on the maximum edge detected there were plenty of exceptions when the algorithm didn't perform well. So, we tried using the Viterbi algorithm for the same. Emission probabilities were such that the closer the pixel to the Bayes net ridge the higher the emission probability. Then we normalized them. The transition probabilities were set such the closer the pixel to the last identified pixel in the ridge, the higher the probability for the model. We applied the Viterbi Algorithm twice and then took the maximum of the two emission probabilities. This takes the best of the 2 cases.

## Part - III
Here we added 1 human identified pixel. We set the probability for that pixel as one and the probability for that pixel in that column as 1 and the probability for other pixels as 0. Then we used this probability to predict the next pixel in the horizon which is done by the Viterbi Algorithm.

#### To run the program: ./horizon.py input_file.jpg row_coord col_coord
