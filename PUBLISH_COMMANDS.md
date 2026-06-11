# Publish Commands

Run these only after final review.

## 1. Review staged files

```bash
cd "C:/Users/ALPHA/Desktop/VIBE CODING PROJECTS/ai-journal-android-case-study"
git status --short
git diff --cached --stat
```

## 2. Commit locally

```bash
git commit -m "Create public AI journal case study"
```

## 3. Create public GitHub repo and push

Recommended public repo name:

```text
ai-journal-android-case-study
```

Using GitHub CLI:

```bash
gh repo create ai-journal-android-case-study --public --source=. --remote=origin --push --description "Public case study for a private Android AI journaling app."
```

If remote already exists:

```bash
git remote add origin https://github.com/dionnblake/ai-journal-android-case-study.git
git branch -M main
git push -u origin main
```

## 4. GitHub repo settings

After publish:

- Add topics: `android`, `kotlin`, `jetpack-compose`, `llm`, `case-study`, `portfolio`
- Enable repository description
- Keep Issues disabled unless you want public questions
- Add demo video link to README after recording

## 5. Do not publish these

- private source code
- real journal entries
- proprietary prompts
- API keys
- monetization logic
- private roadmap
