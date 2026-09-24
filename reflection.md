# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it? 
A: The game look like a number guessing game. We are supposed to guess a number between 1 and 100 within 8 attempts.
- List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards").
A: Two things I noticed was that the hints was backwards ands that
hitting new game gave 8 attempts while starting initially gives 7.
**Bug Reproduction Log**

Document at least 3 bugs you found. Add rows as needed.

| Input                            | Expected Behavior            | Actual Behavior                                          | Console Output / Error | Suspected Code Location    |
|----------------------------------|------------------------------|----------------------------------------------------------|------------------------|----------------------------|
| Guess 50                         | "Too High - Hint"            | "Too Low - Hint"                                         | None                   | app.py:36-40 (check_guess) |
| Secret 9, Guess 80, on 2nd guess | "Too High"                   | "Too Low" (secret compared as a string on even attempts) | None                   | app.py:158-161             |
| Win, then click "New Game"       | Fresh round, can guess again | Still shows "You already won", game stuck                | None                   | app.py:134-138             |

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)? Claude
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result). I asked the AI where the bugs were located and saw to it myself that it was right or wrong.
- Give one example of an AI suggestion you did not accept as written (including what the AI suggested, why you rejected or changed it, and how you verified your version). It does not have to be a suggestion that was wrong: over-engineered, out of scope, harder to read, or a poor fit for this codebase all count.
The AI tried to use a hashmap for the answers which is still technically correct, but we already had a working solution. There was no point to adding it.
HINT_MESSAGES = {
    "Win": "🎉 Correct!",
    "Too High": "📉 Go LOWER!",
    "Too Low": "📈 Go HIGHER!",
}
---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed? 
A: I manually tested to see if the program was working as intended. I.E. Go Higher for a number thats actually higher than the guess.
- Describe at least one test you ran (manual or using pytest)
  and what it showed you about your code.
A: Two tests I added to pytest were testing to see if the right hint message was being used.

- Did AI help you design or understand any tests? How?
A: The AI wrote the test and I verified that they were correctly testing parts of the program.
---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
A: Streamlit reruns the whole script top to bottom on every click, so it forgets everything unless you use session_state — a dictionary that survives reruns and remembers things like the secret number and score.
---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
  A: Asking for an initial understanding of what the program is SUPPOSED to do and what it currently does.
  Additionally, I had pushed the fixes directly to GitHub, skipping pushing the FIXME comments.
- What is one thing you would do differently next time you work with AI on a coding task?
  A: Manually verify a bit more before asking about a specific bug.
- In one or two sentences, describe how this project changed the way you think about AI generated code.
  A: Overall, the project has not changed my mind about AI generated code. I already knew AI generated code needed to be verified and not trusted blindly. One thing I would note is that with how fast AI is, its really easy to not want to read what it's doing as that's the slowest part of the process.