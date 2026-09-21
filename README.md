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

## Development Log for One Pixel Stop 4

Round 1: I asked for the classifier to become a 5-point/question quiz, instead of letting the visitor just do 1 shape at a time. This incentivizes the visitor to engage with the site more. I also added different results based on the final score: Love expert for 5, Love learner for 2-4, and Love yearner for 0-1 points.

Round 2: After testing the quiz, I wanted to make the user experience a bit more special. So, I changed the title from "Make your guess" to "Are you good at love?" Which I think attracts visitors with a competitive streak. I also asked for a separate result screen after all 5 questions, so visitors would clearly see their score, title, description, and a try again button.

Round 3: The shapes were too easy to identify, so I asked for more ambiguous shapes that looked more like hearts. I also noticed that a normal heart was not getting a 100% love score, so I asked why and learned that the percentages represented similarity instead of actual probability. I changed the classifier to render an exact match of 100% to a trained heart.

Round 4: While testing again, I found out that the classifier incorrectly classified one of the heart shapes. I think this is because I added the more ambiguous hearts into the quiz, so I asked to add 3 more ambiguous hearts into the training data. This proved to me that changing training examples can change a classifier's predictions.

Round 5: When the visitor and classifier disagreed, the page did not award a point but it would say it did. I asked for this to be fixed. I also clarified the score is about agreeing with the classifier, not that the classifier is objectively correct.

### Update after Experimenting

I tested the classifier with an upside-down teardrop, and it predicted with a 66% love score. I realized the classifier was not emphasizing the divot at the top of the heart, one of the most identifying features of a heart. So I asked Codex to make it important.

I also improved the page based on testing, putting detailed info under "Show Exact Calculations" so the page wouldn't be overwhelming. I also removed some clues that made the quiz too easy, and changed navigation buttons to be "Next," "See results," and "Try again" instead of just "Try again."

### Update after User Testing

After testing, I realized the page revealed clues about the classifier too early and made the game boring for my visitor. So, I wanted visitors to have a chance to figure out the pattern, so I created a "Hint" section that could reveal a hint word and become more obvious when the visitor disagrees with the classifier multiple times: from "Affection" → "Valentine" → "Divot" → "Heart."

## Credits

Materials are by [Xiuye Chen](https://github.com/xiuyechen), developed with Codex, and shared under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
