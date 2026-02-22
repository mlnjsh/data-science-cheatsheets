# LLM Prompt Engineering Cheatsheet

## Core Techniques

| Technique | Description | When to use |
|-----------|-------------|-------------|
| Zero-shot | Just ask the question, no examples | Simple tasks |
| Few-shot | Provide 2-5 examples before the question | Pattern-following tasks |
| Chain-of-Thought | "Think step by step" | Math, reasoning, logic |
| Self-consistency | Sample multiple answers, take majority | Improve reasoning accuracy |
| Role prompting | "You are an expert data scientist..." | Domain-specific tasks |

## Prompt Structure

```
[System/Role] You are a senior data scientist.
[Context] Given the following dataset with columns: ...
[Task] Analyze the correlation between X and Y.
[Format] Provide your answer as:
1. Summary of findings
2. Statistical test used
3. Recommendations
[Constraints] Use only scipy and pandas.
```

## Few-Shot Template

```
Classify the sentiment of each review.

Review: "Great product, works perfectly!" -> Positive
Review: "Terrible quality, broke after a day" -> Negative
Review: "It's okay, nothing special" -> Neutral

Review: "Absolutely love it, best purchase ever!" ->
```

## Chain-of-Thought

```
Q: If a train travels at 60 mph for 2.5 hours, then 80 mph for 1.5 hours,
   what is the total distance?

Let me solve this step by step:
1. Distance = speed x time
2. First segment: 60 x 2.5 = 150 miles
3. Second segment: 80 x 1.5 = 120 miles
4. Total: 150 + 120 = 270 miles
```

## Best Practices

- **Be specific**: "Summarize in 3 bullet points" > "Summarize"
- **Provide context**: Include relevant data, constraints, background
- **Specify format**: JSON, markdown, table, numbered list
- **Set constraints**: "Do not include...", "Only use..."
- **Iterate**: Refine prompts based on output quality
- **Use delimiters**: Triple backticks, XML tags, or quotes to separate sections
- **Ask for reasoning**: "Explain your reasoning" improves accuracy

## Common Patterns

```
# Structured extraction
Extract the following from the text:
- Name:
- Date:
- Amount:
- Category:

# Code generation
Write a Python function that:
- Input: list of integers
- Output: list of tuples (number, is_prime)
- Include type hints and docstring

# Data analysis
Analyze this CSV data and:
1. Identify the top 3 trends
2. Flag any anomalies
3. Suggest next steps
```

## Pitfalls to Avoid

| Pitfall | Instead |
|---------|---------|
| Vague instructions | Be specific about format and scope |
| Too many tasks at once | Break into sequential prompts |
| No examples for complex tasks | Add 2-3 few-shot examples |
| Ignoring output format | Specify JSON, markdown, etc. |
| Not validating outputs | Ask model to verify its own work |
