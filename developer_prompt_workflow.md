# Developer Prompt Workflow Guide
> The exact prompts every developer should use when building with AI

---

## Table of Contents
1. [Project Setup Prompt](#1-project-setup-prompt)
2. [Feature Building Prompt](#2-feature-building-prompt)
3. [Bug Fix Prompt](#3-bug-fix-prompt)
4. [UI Correction Prompt](#4-ui-correction-prompt)
5. [Paste Documentation Prompt](#5-paste-documentation-prompt)
6. [Code Explanation Prompt](#6-code-explanation-prompt)
7. [State Management Prompt](#7-state-management-prompt)
8. [Security Review Prompt](#8-security-review-prompt)
9. [Performance Check Prompt](#9-performance-check-prompt)
10. [End of Session Commit Prompt](#10-end-of-session-commit-prompt)
11. [Quick Reference Card](#quick-reference-card)
12. [The Golden Rule](#the-golden-rule-for-all-prompts)

---

## 1. Project Setup Prompt
**Use this at the very beginning of any project**

```
I want to build [app name]. Here is what it does:
[2-3 sentences describing the app]

Help me create a complete agents.md file for this project.

My stack:
- Frontend: [React / React Native / Next.js]
- Styling: [Tailwind / CSS]
- Database: [Supabase / Firebase / MongoDB]
- Auth: [Clerk / Firebase Auth]
- State: [Zustand / Redux]

The file should include:
- My role as an AI assistant
- App overview
- Full stack details
- Folder structure
- Styling rules
- Patterns to follow
- Common mistakes to avoid

Ask me questions if anything is unclear before generating it.
```

---

## 2. Feature Building Prompt
**Use this for every single new feature**

```
Read agents.md first and follow it strictly 
without exceptions.

Task: Build [one specific feature]

Details:
- [What it should look like]
- [What data it uses]
- [How user interacts with it]

Constraints:
- Do not change [existing thing that works]
- Do not install new libraries without asking
- Do not modify [specific file or component]
- If anything is unclear, ask before coding

[Attach design screenshot if visual]
```

**Real example:**
```
Read agents.md first and follow it strictly 
without exceptions.

Task: Build the Add Task form

Details:
- Form with 3 fields: task name, deadline, client name
- Submit button saves to Supabase tasks table
- After submit, clear the form and show success message

Constraints:
- Do not change the existing TaskList component
- Do not modify the Supabase client in /lib/supabase.ts
- Keep existing Tailwind color scheme
- Ask me before adding any new library
```

---

## 3. Bug Fix Prompt
**Use this when something breaks**

```
Read agents.md first and follow it strictly.

Problem: [Describe exactly what is broken]

Expected behavior: [What should happen]

Current behavior: [What is actually happening]

Error message: [Paste exact error here]

Constraints:
- Fix only this specific issue
- Do not change anything else
- Do not refactor working code
```

**Real example:**
```
Read agents.md first and follow it strictly.

Problem: The deadline date picker is not showing 
on mobile screens

Expected behavior: Date picker should appear 
above the keyboard when user taps the field

Current behavior: Date picker appears behind 
the keyboard and is not visible

Error message: No error, just UI issue

Constraints:
- Fix only the date picker positioning
- Do not touch any other form fields
- Do not change the form layout
```

---

## 4. UI Correction Prompt
**Use this when design does not match what you wanted**

```
Read agents.md first and follow it strictly.

The [component name] does not look right.

Current problem:
[Describe what looks wrong]

What I want instead:
[Describe exactly what you want]

Constraints:
- Only change the styling of this component
- Do not touch the logic or data fetching
- Keep all existing Tailwind classes that work

[Attach screenshot of current state]
[Attach screenshot of what you want]
```

---

## 5. Paste Documentation Prompt
**Use this when AI uses outdated library code**

```
Read agents.md first and follow it strictly.

Task: [What you want to implement]

Important: The AI training data may be outdated 
for this library. Use ONLY the documentation 
provided below, not your training data.

Constraints:
- Follow the exact API shown in docs below
- Do not use deprecated methods
- Do not change existing working code

--- DOCUMENTATION START ---
[Paste the copied docs from the library website]
--- DOCUMENTATION END ---
```

---

## 6. Code Explanation Prompt
**Use this when you don't understand what AI built**

```
Explain each file you just generated in simple language.

For each file tell me:
- What does this file do
- Why did you create it this way
- What would break if I deleted it
- Is there anything I should know about maintaining it

Do not use technical jargon. 
Explain it like I am a smart person 
who is not a developer.
```

---

## 7. State Management Prompt
**Use this for features that need to save data**

```
Read agents.md first and follow it strictly.

Task: Add state management for [feature]

Behavior I want:
- When user does [action], save [data] to state
- When app reopens, restore [data] from storage
- If [condition], redirect user to [screen]
- If [other condition], show [screen]

Constraints:
- Use [Zustand / Redux] as defined in agents.md
- Do not create a new state library
- Preserve existing UI exactly
- Add a temporary clear button so I can test the flow

Ask me before making any architecture decisions.
```

---

## 8. Security Review Prompt
**Use this before shipping any feature with user data**

```
Read agents.md first and follow it strictly.

Review the code we just built for security issues.

Check specifically:
- Are any API keys or secrets exposed in the frontend
- Is user authentication properly verified
- Can one user access another user's data
- Are all inputs validated before saving to database
- Are there any SQL injection risks

For each issue found:
- Explain the risk in simple language
- Show me exactly how to fix it
- Do not change anything else while fixing
```

---

## 9. Performance Check Prompt
**Use this when app feels slow**

```
Read agents.md first and follow it strictly.

The [screen or feature] feels slow.

Check for:
- Unnecessary re-renders
- Data being fetched too many times
- Large images not being optimized
- Missing loading states confusing the user

For each issue:
- Explain why it causes slowness
- Fix only that specific issue
- Show me the before and after difference

Do not refactor working code while fixing performance.
```

---

## 10. End of Session Commit Prompt
**Use this before closing your editor**

```
We just finished building [feature name].

Help me write a clear Git commit message that explains:
- What was built
- What files were changed
- Why these changes were made

Format: 
feat: [short description]

Details:
- [file 1]: [what changed]
- [file 2]: [what changed]
```

---

## Quick Reference Card

```
START OF PROJECT
└── Use Prompt 1 (Project Setup)

BUILDING FEATURES
└── Use Prompt 2 (Feature Building)
└── Use Prompt 4 (UI Correction) if needed
└── Use Prompt 5 (Paste Docs) if library is outdated

WHEN THINGS BREAK
└── Use Prompt 3 (Bug Fix)

UNDERSTANDING CODE
└── Use Prompt 6 (Code Explanation)

DATA AND STATE
└── Use Prompt 7 (State Management)

BEFORE SHIPPING
└── Use Prompt 8 (Security Review)
└── Use Prompt 9 (Performance Check)

END OF EVERY SESSION
└── Use Prompt 10 (Commit Message)
```

---

## The Golden Rule for All Prompts

> Always **start** with:
> **"Read agents.md first and follow it strictly"**
>
> Always **end** with:
> **"Ask me before making any decisions I did not mention"**

These two lines alone will save you hours of fixing AI mistakes.

---

*Based on the Practical Vibe Coding workflow — build fast, stay structured, ship confidently.*
