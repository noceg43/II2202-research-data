# Scenarios

# Scenarios: steps and paths

The **Expected feedback** column comes from the cognitive-walkthrough preparation: for every action you state what the system should show afterwards, so that question 4 ("will the user see that progress is being ade?") is answered against an expectation, not against whatever happened.

## Persona

Kim, 27, master's student in an unrelated field. Has used a chatbot a few times, always by copying prompts found online. Knows what a chat input is; does not know the product's modes, models or attachment features. Reads English. Assumes nothing about refreshable or dismissible suggestions.

**Preconditions:** new conversation, same account throughout, English interface, Swedish locale, web in a default desktop viewport or the default mobile app.

## S1 — Write a professional email

**Goal.** Kim asks a course administrator for a three-day extension, from an empty chat.

**Task end.** A draft that can be sent with light editing.

| ID | Step | When | Component | Expected feedback |
| --- | --- | --- | --- | --- |
| A01 | Read the empty-state area | always | empty-state area | Greeting, composer and any affordance visible without scrolling |
| A02 | Read the text of each displayed example | if examples exist | prompt suggestions | The example text is readable in place |
| A03 | Compare the examples with the email task | after A02 | prompt suggestions | Examples are distinguishable by the task they suggest |
| A04 | Select the matching example | if A03 = match | prompt suggestions | The selection is visibly marked, or the text moves into the field |
| A05 | Compose the request (recipient, deadline, reason, tone) | if A03 = no match | input field | The typed text appears in the field |
| A06 | Edit the selected example | if A04 ran and wording is close | input field | The edited text replaces the example in the field |
| A07 | Send | after A04, A05, A06 or A14 | send control | The message leaves the field and a pending state appears |
| A08 | Check that the text appears as the user's message | after A07 | user message bubble | The submitted text is visible as the user's message |
| A09 | Check that a response started | after A08 | response card | A placeholder, a streaming answer or the first lines appear |
| A10 | Read the response | after A09 | response card | The full response is readable |
| A11 | Judge whether it is usable | after A10 | response card | No system feedback; the judgement is internal |
| A12 | Select a capability entry that matches the task | if capability entries exist | capability menu | The entry is visibly selected and a submenu appears |
| A13 | Select an entry in the capability submenu | after A12 | capability submenu | The entry is marked and its template appears in the field |
| A14 | Add own content to the injected template | after A13 | input field | Template plus added text visible in the field |
| A15 | Close the capability panel without selecting an entry | if A12 = no match | capability menu | The panel closes and the composer returns to its default state |
| A16 | Select an autocomplete completion while typing | if completions appear during A05 | autocomplete list | The completion fills the field; nothing is sent until Send |

```
P1  = A01 A02 A03 A04 A07 A08 A09 A10 A11          example used
P1e = A01 A02 A03 A04 A06 A07 A08 A09 A10 A11      example edited
P2  = A01 A02 A03 A05 A07 A08 A09 A10 A11          written from scratch
P3  = A01 A12 A13 A14 A07 A08 A09 A10 A11          capability template
```

Steps A15 and A16 are not part of any path: they are recorded where they happen in a run (added after the first web runs).

## S2 — Summarise a document

**Goal.** Kim has the KTH syllabus PDF for a course and wants to know what is required to pass, how it is graded, and whether the document states any deadlines or exam dates.

**Task end.** A summary covering requirements and grading, or a clear statement that the document does not say.

| ID | Step | When | Component | Expected feedback |
| --- | --- | --- | --- | --- |
| A01 | Read the empty-state area | always | empty-state area | Greeting, composer and any affordance visible without scrolling |
| A02 | Read the text of each displayed example | if examples exist | prompt suggestions | The example text is readable in place |
| A03 | Judge whether an example implies a document | after A02 | prompt suggestions | Examples are distinguishable by the task they suggest |
| A04 | Open the attachment affordance | before or after composing | attachment control | A menu or picker opens with a file option |
| A05 | Select the document from the device | after A04 | file picker | The device picker opens and accepts the file |
| A06 | Check that the file is attached | after A05 | attachment indicator | The file name is shown as attached |
| A07 | Compose an instruction naming the document and the focus | if A03 = no match | input field | The typed text appears in the field |
| A08 | Select the example that presumes a document | if A03 = match | prompt suggestions | The example is placed in the field or sent |
| A09 | Send | after A06 and A07 or A08 | send control | The message leaves the field and a pending state appears |
| A10 | Check the instruction as the user's message | after A09 | user message bubble | The instruction is visible as the user's message |
| A11 | Check that a response started | after A10 | response card | A placeholder, a streaming answer or the first lines appear |
| A12 | Read the summary | after A11 | response card | The full summary is readable |
| A13 | Check the summary against the document: requirements, grading, dates | after A12 | response card | The content needed for the comparison is visible |
| A14 | Judge whether it is usable | after A13 | response card | No system feedback; the judgement is internal |
| A15 | Check that the attachment is shown as attached in the conversation | after A10 | attachment card | The file is visibly attached in the conversation |
| A16 | Select an autocomplete completion while typing | if completions appear during A07 | autocomplete list | The completion fills the field; nothing is sent until Send |

```
P1 = A01 A02 A03 A08 A04 A05 A06 A09 A10 A15 A11 A12 A13 A14   example first
P2 = A01 A02 A03 A07 A04 A05 A06 A09 A10 A15 A11 A12 A13 A14   prompt first
P3 = A01 A02 A03 A04 A05 A06 A07 A09 A10 A15 A11 A12 A13 A14   attach first
```

Steps A16 are not part of any path: they are recorded where they happen in a run (added after the first web runs).

**Why this scenario.** It is the case where the start is not carried by a suggestion, which is the "alternative affordance" condition. `P3` exists here and not in S1.

## S3 — Plan a weekend trip

**Goal.** Kim wants a two-day plan with a budget and an interest in walking.

**Task end.** A plan covering both days and the constraints, after one refinement turn.

**Status.** 18 steps (A15–A18 recorded outside the paths), 2 paths, walked on the four web products on 2026-11-19.

| ID | Step | When | Component | Expected feedback |
| --- | --- | --- | --- | --- |
| A01 | Read the empty-state area | always | empty-state area | Greeting, composer and any affordance visible without scrolling |
| A02 | Read the text of each displayed example | if examples exist | prompt suggestions | The example text is readable in place |
| A03 | Judge whether an example fits trip planning | after A02 | prompt suggestions | Examples are distinguishable by the task they suggest |
| A04 | Select the matching example | if A03 = match | prompt suggestions | The selection is visibly marked, or the text moves into the field |
| A05 | Compose the request with destination, days, budget, interests | if A03 = no match | input field | The typed text appears in the field |
| A06 | Send | after A04 or A05 | send control | The message leaves the field and a pending state appears |
| A07 | Check that the text appears as the user's message | after A06 | user message bubble | The submitted text is visible as the user's message |
| A08 | Check that a response started | after A07 | response card | A placeholder, a streaming answer or the first lines appear |
| A09 | Read the plan | after A08 | response card | The plan is readable in full |
| A10 | Check that both days and the constraints are covered | after A09, and after A13 | response card | The content needed for the comparison is visible |
| A11 | Compose an additional constraint | if A10 = incomplete | input field | The typed text appears in the field |
| A12 | Send the refinement | after A11 | send control | The message leaves the field and a pending state appears |
| A13 | Read the updated plan | after A12 | response card | The updated plan is readable in full |
| A14 | Judge whether it is usable | after A10 = acceptable | response card | No system feedback; the judgement is internal |
| A15 | Close the example panel without selecting an entry | if A03 = no match after opening a panel | prompt suggestions | The panel closes and the composer returns to its default state |
| A16 | Select an autocomplete completion while typing | if completions appear during A05 | autocomplete list | The completion fills the field; nothing is sent until Send |
| A17 | Select a follow-up suggestion as the refinement | if A10 = incomplete and suggestions appear, instead of A11 | follow-up suggestions | The suggestion is placed in the field or sent as the user's message, and its effect is clear before selecting |
| A18 | Switch on a mode offered in the composer | optional, before A06 | mode control | The mode is visibly on and its effect is stated |

```
P1 = A01 A02 A03 A04 A06 A07 A08 A09 A10 A11 A12 A13 A10 A14   example first
P2 = A01 A02 A03 A05 A06 A07 A08 A09 A10 A11 A12 A13 A10 A14   written from scratch
```

Steps A15, A16, A17 and A18 are not part of any path: they are recorded where they happen in a run (added after the first web runs).

**Why this scenario.** It tests what happens after the first answer, where follow-up suggestions appear. `A10` is visited twice: that is the loop, not a second step.

## What is still open

1. Three scenarios or four.
2. Which go/no-go rule is the official one.