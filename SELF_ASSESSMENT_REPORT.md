# Self-assessment - IA#2 (Session 4: Dynamic Catalogue)
Submitted by: 24120417 Lưu Đình Quân

Total I claim: 93/100

| Criterion | Max | I claim | Evidence |
|---|---|---|---|
| Behaviour | 45 | 45 | All 8/8 test cases passed in browser console via `selfCheck()`; event delegation on `#catalogue` works; search is case-insensitive; XSS prevented using `textContent`; form submit event prevents page reload (`e.preventDefault()`); dynamic cart total and item count calculated correctly including loaded items. |
| Scope | 10 | 10 | Only `index.html` and `app.js` were modified. `style.css` and `check.js` remain completely untouched. |
| Brief | 15 | 12 | `brief.md` contains exact sequential prompts given to the AI Assistant covering all technical constraints (DOM id/class retention, scope limits, Event Delegation, `textContent` for XSS prevention, form submit reload protection, and `selfCheck()` completion criteria). |
| AI-LOG.md | 20 | 17 | `AI-LOG.md` updated with individual entries for Parts A, B1, B2, B3, and B4 using the required format (`Tool`, `Asked for`, `Kept`, `Changed`, `Rejected`) and cross-referenced with rows in the `Done means` table. |
| Commit History | 10 | 8 | Clean sequential Git history starting from `init project`, followed by individual commits for `Part A`, `Part B1`, `Part B2`, `Part B3`, and `Part B4` (`git log --oneline`). |

**What I did not manage**

Although the implementation appears to satisfy the main functional requirements, I am not fully confident that every requirement has been independently verified beyond the available self-check results. I also initially allowed the AI Agent to implement all Part B features in a single pass, which did not follow the incremental workflow I intended to use.

**What I would do differently**

In future tasks, I will ask the AI Agent to implement and verify each sub-task separately before proceeding to the next one. I will also create and review a Git commit after completing each sub-task, rather than relying on later adjustments to organize the commit history. Finally, I will maintain a clearer mapping between each requirement, its implementation, and the corresponding test evidence so that my self-assessment is more accurate and defensible.