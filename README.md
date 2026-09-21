# Love or Fake Love?

## Name and purpose

**Love or Fake Love?** is a playful, five-question shape classifier quiz. Visitors label random shapes as “love” or “fake love” and compare their guesses with the classifier. The idea is to associate heart shapes with “love,” including some unusual hearts that are harder to recognize.

The page teaches how training examples and the features a classifier looks for affect its predictions. It is a shape game, not a way to judge real feelings.

## How to open and use the page

1. Download or clone this repository. If you download a ZIP, extract it first.
2. Open `index.html` in Chrome, Safari, or Firefox by double-clicking the file. Use the browser rather than VS Code’s preview.
3. Look at the shape and choose **Love** or **Fake love**.
4. Compare your guess with the prediction and its two percentage scores. Open **Hint** for a clue or **Show Exact Calculations** for the evidence.
5. Click **Next** to continue. After question five, click **See results**, then **Try again** to restart.

You earn one point whenever your guess agrees with the classifier:

- **5 points:** Love expert
- **2–4 points:** Love learner
- **0–1 points:** Love yearner

Hints get more direct after repeated disagreements. Everything runs in one HTML file, with no installation, API keys, paid services, or internet connection needed. `one-pixel.html` is the original starter page; `index.html` is the finished quiz.

## How it makes a prediction

The classifier compares a small picture of each shape with nine labeled training examples: six hearts labeled “love,” plus a circle, oval, and square labeled “fake love.” The hearts include regular, small, big, shallow-dip, narrow, and uneven versions. Shapes are drawn at a standard size for comparison, so display size does not affect the prediction.

It combines two clues:

- **Top dip (70 points):** It checks the picture for a divot at the top, where the middle dips below both sides. If it detects one, it adds 70 love points; otherwise, it adds zero.
- **Outline similarity (up to 30 points):** It compares the picture with the closest example in each label group. A closer match to the love examples contributes more love points.

The love points become the love percentage. The fake love percentage is 100 minus that number. A love score above 50% produces “love”; otherwise, the prediction is “fake love.” These are comparison scores, not measured probabilities of being correct.

**Show Exact Calculations** reveals the detected feature, the specific closest training example, and how the points add up. The examples teach it about outlines, while the importance of the top dip is a rule added during development.

## One limitation I discovered

An upside-down teardrop once received about 66% love because its outline resembled the heart examples, even though it had no top dip. I added the top-dip feature to address this. Now a shape without a detected dip cannot score above 30% love.

This still does not make the classifier perfect: its strong preference for a top dip could reject a rotated heart or a heart with a dip too subtle to detect. Quiz points measure agreement with the classifier, not whether the visitor is objectively right.

## Short development log

1. **Five-question quiz:** I changed the single-shape activity into a five-question quiz and added Love expert, Love learner, and Love yearner results to encourage visitors to keep playing.
2. **Results screen:** I changed the title to “Are you good at love?” to appeal to visitors’ competitive streak and added a separate screen for the final score and description.
3. **Trickier shapes and scores:** I added more ambiguous shapes. I noticed that a regular heart did not get 100% love and learned that the scores represented similarity, not actual probability. I adjusted the scoring so an exact training match could receive 100% love.
4. **More training examples:** After an unusual heart was classified incorrectly, I added three unusual hearts to the training data. This showed me that changing the examples can change predictions.
5. **Consistent quiz points:** I noticed that a visitor could earn a point even when the classifier disagreed. I changed the scoring so points consistently reward agreement and explained that the classifier can still be wrong.
6. **Feature evidence:** After testing the upside-down teardrop, I made the top dip an important feature and added visible calculations and the name of the closest training example.
7. **Final interface testing:** I put detailed evidence under “Show Exact Calculations,” added optional hints that get clearer after disagreements, and used “Next” between questions and “Try again” to restart.

## Credits

Based on CPSC 1710 starter materials by [Xiuye Chen](https://github.com/xiuyechen), shared under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Quiz developed with assistance from Codex.
