# Acceptance criteria — FitFindr

Five criteria that say what "working" means for this agent, written in unit 3
**before** any results existed.

An acceptance criterion names a target: a number, a count, a rate, or something
a person could plainly observe. *"The agent handles errors"* is an opinion.
*"When search returns nothing, the agent stops before calling the second tool,
in 5 of 5 tries"* is a criterion.

Under each one, write a sentence or two on **why that target** and not a
stricter one. A reason that says something about your tools, your loop, or the
data earns credit; *"80% seemed reasonable"* does not.

> Missing your own targets next unit costs you nothing. Setting a target so
> easy you can't miss it does.

**Two are written for you. You write three.**

---

## 1. A matching query completes all three tools

Given a query that matches at least one listing, the agent completes all three
tool calls and returns a fit card — in at least 4 of 5 tries.

**Why this target:**
The 4-of-5 target allows for occasional failures because the search uses keyword matching, which may not recognize every description of an item. Model calls may also fail occasionally. Requiring 5 of 5 successful attempts would be stricter than necessary for this initial implementation.

---

## 2. An impossible query stops before the second tool

Given a query that matches no listings, the agent stops before calling
`suggest_outfit` and returns a message naming what to change — 5 of 5 tries.

**Why this target:**
The 5-of-5 target is reasonable because the agent only needs to check whether the search result is empty. This is a simple condition controlled by the code and does not depend on an AI-generated response. Therefore, the agent should stop correctly every time no matching item is found.

---

## 3. The agent passes the correct selected item between tools

In 5 out of 5 tests, the listing ID stored in `session["selected_item"]` must match the listing ID received by `suggest_outfit()`.

**Why this target:**

The 5-of-5 target is necessary because the agent must recommend an outfit using the same item selected during the search. Passing a different item would produce an incorrect recommendation. Since session state is controlled by the program, the IDs should match every time.


---

## 4. The fit card mentions the correct item and price

In 5 out of 5 tests, the generated fit card must mention the selected clothing item and its correct price.

**Why this target:**

The 5-of-5 target is important because customers need accurate information about the clothing they want to purchase. Although AI-generated captions may vary in wording, the selected item and its price should remain correct in every caption.



---

## 5. Search results respect the user's maximum price

In 5 out of 5 tests, every clothing item returned by `search_listings()` must have a price less than or equal to the user's specified maximum price.

**Why this target:**

The 5-of-5 target is reasonable because price filtering uses a simple numerical comparison. Customers should not receive recommendations that exceed their budgets. Since the code controls this condition, it should work correctly in every test.



---

<!-- ─────────────────────────────────────────────────────────────────────────
     UNIT 4 — read this before you change anything above.

     If a criterion turns out to be BROKEN rather than merely unmet, you can
     revise it, and that earns credit. But never delete or edit the original
     line. Add the revision underneath it, like this:

         ## 4. Something about the fit card

         The fit card is different every time.

         **Why this target:** ...

         > **Revised in unit 4:** For 5 different items, the 5 fit cards share
         > no opening sentence.
         >
         > **Why revised:** "different" wasn't checkable — two cards that
         > differed by one word still counted. The new version is something I
         > can actually score.

     That's a revision because the criterion couldn't be MEASURED.

     Lowering a target because you missed it is not a revision, and it costs
     you the point:

         ✗ "I said the empty search stops it 5 of 5 times, but I got 3 of 5,
            so 3 of 5 is more realistic."

     A number you missed stays where it is, gets diagnosed, and gets a fix
     attempted. That's where the points are.
     ───────────────────────────────────────────────────────────────────────── -->
