# Copilot Instructions 

## How to Use This Repo with AI

1. Put your raw content file in the `input/` folder.
   - Example: `input/my-raw-content.txt`

2. Choose a prompt from the `prompts/` folder.
   - Example: `prompts/user-story-prompt-template.md`

3. Run your AI agent (like Copilot) to apply the chosen prompt to your input file.
   - The agent should read the input file, use the prompt, and generate a markdown result.

4. Save the result in the `output/` folder as a markdown file.
   - Example: `output/my-processed-content.md`

## Example Workflow

- Input: `input/requirements.txt`
- Prompt: `prompts/visionary-press-release.md`
- Output: `output/visionary-press-release.md`

## Folder Structure
- `input/` — Place your raw files here
- `prompts/` — Choose a prompt to apply
- `output/` — AI-generated markdown files go here

## Tips
- Keep input files simple (plain text or markdown)
- Prompts should be clear and focused
- Output files are always markdown

## Output File Formatting Guidelines

When creating markdown output files, ensure clean presentation:

### DO:
- Create clean, properly formatted markdown without code block wrappers
- Remove all HTML comments (`<!-- -->`) from the final output
- Remove template metadata and instructional comments
- Use proper markdown headers, lists, and formatting
- Include a brief subtitle or context line that references the input file (e.g., "*Based on [input/filename.txt]*" or "*Generated from [input/source-file.md]*")
- Link back to the original input file when possible for traceability

### DON'T:
- Wrap the entire content in markdown code blocks (```markdown)
- Include template instructions or AI assistant guidance in the output
- Leave HTML comments scattered throughout the document
- Include licensing boilerplate unless specifically requested
- Create files that look like templates rather than final deliverables

### Example Structure:
```
# Clear Title

*Brief context if needed*

## Main Content Section

Clean, properly formatted content without template artifacts.
```

The goal is presentation-ready documents that render cleanly in markdown preview.

