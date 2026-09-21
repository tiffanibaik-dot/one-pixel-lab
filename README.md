# CPSC 1710 Labs

Student-facing assignments and starter materials for CPSC 1710, Fall 2026.

## Labs

- [Lab 1: Meet a deep-learning notebook](lab-01/)
- [Lab 2: From one pixel to your classifier](lab-02/)

Use the [live course hub](https://xiuyechen.github.io/cpsc1710-labs/) for the simplest experience. Each assignment is available as a webpage and a printable PDF.

## Opening the files

The HTML files have no build step. After cloning, open `index.html` directly in Chrome, Safari, or Firefox. Avoid VS Code's **Open Preview** for these files: its internal `file+.vscode-resource` links do not work as normal browser addresses.

You can also serve the repository locally:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000/`.

## Credits

Materials are by [Xiuye Chen](https://github.com/xiuyechen), developed with Codex, and shared under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

## Development Log for One Pixel Stop 4

Round 1: I asked for classifier to become a 5-point/question quiz, instead of letting the visitor just do 1 shape at a time. This incentivizes the visitor to engage with the site more. I also added different results based on the final score: Love expert for 5, Love learner for 2-4, and Love yearner for 0-1 points.

Round 2: After testing the quiz, I wanted to make the user experience a bit more special. So, I changed the title from "Make your guess" to "Are you good at love?" Which I think attracts visitors with a competitive steak. I also asked for a separate result screen after all 5 questions, so visitors would clearly see their score, title, description, and a try again button.

Round 3: The shapes were too easy to identify, so I asked for more ambiguous shapes that looked more like hearts. I also noticed that a normal heart was not getting a 100% love score, so I asked why and learned that the percentages represented similarity instead of actual probability. I changed the classifier to render an exact match of 100% to a trained heart. 

Round 4: While testing again, I found out that th eclassifier incorrectly classified one of the heart shapes. I think this is because I added the more ambiguous hearts into the quiz, so I asked to add 3 more ambiguous hearts into the training data. This proved to me that changing training examples can change a classifier's predictions.

Round 5: When the visitor and classifier disagreed, the page did not award a point but it would say it did. I asked for this to be fixed. I also clarified the score is about agreeing with the classifier, not that the classifier is objectively correct.