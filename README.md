# Debit Dash

A FAR CPA study game inspired by endless runners. You play as an accountant racing home through a ledger-paper track. Dodge accounting obstacles, collect coins, and answer study questions at checkpoints along the way.

The whole game is one self-contained `index.html` file (HTML, CSS, and JavaScript on a canvas), with no libraries, images, or fonts to load.

**Play it:** https://macyschmidt4.github.io/debit-dash/

> If the link doesn't load, turn on GitHub Pages in **Settings → Pages** (Source: *Deploy from a branch*, Branch: `main`, folder `/ (root)`). You can also download `index.html` and open it in any browser.

## How to play

- **Start:** press **Space** or tap the screen.
- **Switch lanes:** **← / →** arrow keys or **A / D** on a keyboard; **swipe left/right** on a phone.
- **Dodge obstacles:** paper stacks, past-due invoices, and impaired buildings. Each hit costs 1 of your 3 hearts, followed by a brief moment of invincibility.
- **Score points:** distance traveled adds points, each **$ coin** is **+10**, and each correct checkpoint answer is **+100**.
- The game speeds up gradually over about 2 minutes. It always leaves at least one open lane with enough time to reach it.
- Your **high score** and **most-missed topics** are saved in your browser and shown on the start screen. Use **Reset Stats** there to clear them.

## How questions work

- After about 8 seconds of running, and then every 12 seconds of running after that, the game freezes at a **checkpoint** and shows a multiple-choice question.
- Answer by clicking/tapping a choice or pressing **1**, **2**, or **3**.
  - **Correct:** +100 points, then the run resumes after a 3-2-1 countdown.
  - **Wrong:** the correct answer and an explanation are shown, and you lose 1 heart. Press **Continue** when you're ready. Losing your last heart this way ends the game.
- Questions are shuffled every game, and the three answer choices are shuffled every time a question appears. Once every question has been used, the deck reshuffles.
- The **Game Over** screen lists every question you missed that game, with the correct answer and explanation, so you can review.
- Every miss is also counted by **topic** across games, and the top 3 appear as **Most Missed Topics** on the start screen.

## Replacing the questions

All questions live in the `QUESTIONS` array near the top of the `<script>` in `index.html` (look for the `QUESTIONS` comment header). Each question is one object:

```js
{
  topic: "Journal Entries",                       // shown on the card; used for Most Missed Topics
  question: "A company buys supplies on account. What is the entry?",
  correct: "Debit Supplies, Credit Accounts Payable",
  wrong1: "Debit Accounts Payable, Credit Supplies",
  wrong2: "Debit Supplies, Credit Cash",
  explanation: "Supplies (an asset) increase with a debit. Buying on account means the company owes money, so Accounts Payable is credited."
},
```

To use your own questions:

1. Open `index.html` and find `const QUESTIONS = [`.
2. Replace, edit, or add objects using the same six fields. Every field is required, and each question needs exactly one correct answer and two wrong answers.
3. Keep the topic names consistent (for example, always `"Leases"`, not sometimes `"Lease Accounting"`) so the Most Missed Topics counts group correctly.
4. Put a comma after each object and wrap text in double quotes. If an answer itself contains a double quote, escape it as `\"`.
5. Save, commit, and push. GitHub Pages updates the live game within a minute or two (do a hard refresh if you still see the old version).

There's no limit on how many questions you can add. The order and answer positions are randomized automatically, so you don't need to mix up where the correct answer goes.

## Coming next

- Replace the placeholder questions with FAR questions from my Becker MCQ review.
