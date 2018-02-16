# Machine Learning Assignment 5
### Feature Extractor

Dan Nguyen

#### Goals

- Create a feature extractor using microbit to detect left and right tilt, and upward swings

#### Tools

- Microbit
- Wekinator
- WekiInputHelper

#### What I did

I found that creating features for left and right tilt were very easy. A little bit harder was getting it to not classify as left or right while sitting still, but with some trial and error I got it to not classify as left or right while holding the Microbit semi-still at ~0º tilt.

When trying to classify upward swing, in my previous attempts, I was trying to collect data very quickly while swinging the device up after hitting record, and then stopping recording data when the swing was complete. Due to my lack of superhuman talent my data for up swings were bad and looked like they didnt work.

#### ML Decisions

Thats where WekiInputHelper came into play. After watching the videos, I was excited to know that the tool made it easy to only send signal when a certain threshold was met. Instead of using Z coordinates, I used *second order difference* on the Z value which allowed me to fine tune my training data for upswings based on acceleration. 

With Cross-validation accuracy with 10 folds I achieved 100% accuracy for tilt using K-nearest Neighbor, k=1

and .02 (RMS) for Swing 



| Feature | Algorithm                                                    | Method           | Result    |
| ------- | ------------------------------------------------------------ | ---------------- | --------- |
| Tilt    | K-means (5)                                                  | Cross-Validation | 99.93%    |
| Tilt    | Support Vector Machine <br>(Complexity constant = 1, Exponent = 2) | Cross-Validation | 100%      |
| Tilt    | Decision Tree                                                |                  | 99.3%     |
| Swing   | Neural Network                                               | Cross-Validation | .02 (RMS) |
| Swing   | Polynomial Regression                                        | Cross-Validation | .02 (RMS) |



