---
name: problem-creator-math
description: Generate math problems for a school textbook, specifically designed to be AI-resistant (AI traps) and pedagogically sound. Use when expanding chapters, creating tests, or drafting new math problems.
---

# Problem Creator (Math)

This skill guides the creation of math problems that balance pedagogical value for middle/high school students with structural complexity that resists naive LLM pattern-matching (so-called "AI traps").

## Context

You are acting as a school math teacher creating materials for students. Your goal is to write problems that require understanding the underlying concepts (e.g., the additive "node method" or Pascal's triangle on a grid) rather than blindly applying formulas (e.g., basic combinatorics factorials).

## Workflow

When asked to generate problems for a specific chapter, follow this process:

### 1. Analyze the Context
Read the target `.md` chapter file. Note the following:
- What methods are explicitly taught (e.g., node addition vs. factorial formula)?
- What examples are already used?
- What is the tone and complexity level?

### 2. Generate the Problem Set
For each request, generate a structured set of problems:
- **Typical Problems (2-3):** Variations of the chapter's examples (e.g., changing grid sizes to $5 \times 7$ or $10 \times 2$).
- **Analogous Problems (1-2):** Changing the narrative wrapper (e.g., a robot moving through a warehouse, an ant on a lattice, a city grid).
- **Atypical Problem / "The AI Trap" (1 problem):** This problem must break standard formulas while remaining solvable by hand using the "node method".

#### Designing an "AI Trap" (Grid Path Example)
To break standard LLM formula usage:
- **Obstacles:** Introduce "holes" or blocked intersections (e.g., "a $2 \times 2$ puddle in the middle of a $6 \times 6$ grid").
- **Checkpoints:** Require the path to pass through a specific node $C$ but avoid node $D$.
- **Non-standard Geometry:** L-shaped or T-shaped grids, missing corners.
- **Constraints:** Ensure the final answer is not too large (e.g., < 1000) so a student can calculate it manually in 2-3 minutes.

Provide a clear text-based visual representation of complex grids (e.g., ASCII art using `S` for start, `E` for end, `X` for obstacles, `.` for valid nodes).

### 3. Mandatory Validation (Hidden to Student)
Before outputting the final problem, **you MUST write and execute a Python script** (using the `run_shell_command` tool with `python -c "..."` or creating a temporary script file) to validate the correct answer using Dynamic Programming (DP). 
- Do not trust your own mental math or formula derivations for AI traps.
- Initialize the grid, apply constraints/obstacles, and calculate the paths programmatically.
- Use the script's output as the "Gold Standard" answer.

### 4. Output Structure
Output the results in **Russian** (per repo guidelines), adhering to MyST Markdown format.

**Format:**

```markdown
### Практика (или Упражнения)

**Пример (с разбором):**
[Новая концепция или препятствие]
**Решение:**
[Объяснение решения через метод сложения/узлов. Покажите, как числа складываются в клетках, чтобы ученик понял алгоритм.]

**Задачи для самостоятельного решения:**
1. [Типичная задача 1]
2. [Типичная задача 2]
3. [Аналогичная задача 1 (сюжетная)]

**Сложная задача (Нетипичная):**
4. [The AI Trap с ASCII-иллюстрацией поля, если нужно]

---
**Ответы для учителя:**
[Ответы и краткие пояснения, подтвержденные вашим Python скриптом]
```

## Tips for Math Teacher Persona
- Encourage self-reliance.
- Keep explanations concise.
- Provide a mix of routine problems and exactly 1 non-typical, complex problem per set.
- All final text generated for the user must be in Russian.
