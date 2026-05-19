# Quick Start - 5 Minute Overview

Get up to speed with this fine-tuning project in 5 minutes.

## What Is This Project?

This project demonstrates **fine-tuning a language model** (GPT-4.1) for a specialized use case: a travel agency chat application.

**Key finding**: Fine-tuned models maintain consistent personality better than prompt engineering alone.

## The Problem We Solved

Building a travel chat that:
- Suggests destinations and activities
- Uses consistent, friendly, inspiring tone
- Never recommends hotels/flights/restaurants
- Asks engaging questions

❌ **Prompt engineering alone** = inconsistent tone, mechanical behavior  
✓ **Fine-tuning with examples** = consistent personality, natural engagement

## What You'll Find Here

| File | Purpose |
|------|---------|
| **README.md** | Full project overview |
| **SETUP.md** | Step-by-step instructions to replicate |
| **FINDINGS.md** | Detailed comparison and analysis |
| **results/** | Test responses and metrics |
| **training_data/** | Sample training data format |

## The Results (TL;DR)

### Training Metrics
✓ Loss: 0.03 (very good)  
✓ Accuracy: 100%  
✓ Time: 1h 24m  

### What Changed
| Metric | Base | Fine-tuned |
|--------|------|-----------|
| Tone | Neutral | Enthusiastic |
| Consistency | Variable | Constant |
| Personality | Instructed | Learned |
| User Experience | Good | Excellent |

## Example: "Where in Rome should I stay?"

### Base Model Response (with instructions):
> I can help you understand the characteristics of different neighborhoods... Are you more interested in history, food, shopping, or nightlife?

*Tone: Formal, structured, asking questions*

### Fine-Tuned Model Response:
> When in Rome, consider staying near the historic center so you can easily explore iconic sites like the Colosseum... What type of activities are you interested in? This will help me suggest the perfect area for you to stay.

*Tone: Friendly, immediately useful, engaging*

## How to Implement (High Level)

1. **Create Foundry Project** (5 min)
   - Sign in to https://ai.azure.com
   - Create new project in North Central US or Sweden Central

2. **Deploy Base Model** (5 min)
   - Search gpt-4.1 in model catalog
   - Deploy using defaults

3. **Test Base Model** (10 min)
   - Ask test questions
   - Notice inconsistent tone

4. **Start Fine-tuning** (2 min)
   - Use training data from [training_data/travel-finetune-hotel.jsonl](training_data/travel-finetune-hotel.jsonl)
   - Submit fine-tuning job
   - **Wait: 60-90 minutes**

5. **Test Fine-tuned Model** (10 min)
   - Ask same questions
   - Notice consistent personality

6. **Compare Results** (10 min)
   - See the difference
   - Validate fine-tuning was worthwhile

**Total Time: ~90 minutes** (mostly waiting for training)

## Key Files to Read

Start with these in this order:
1. **README.md** - Understand the project
2. **SETUP.md** - Follow instructions step-by-step
3. **FINDINGS.md** - Understand the results
4. **results/finetuned_model_responses.md** - See the difference

## Training Data Format

Simple JSONL format - one JSON per line:

```json
{
  "messages": [
    {"role": "system", "content": "You are an AI travel assistant..."},
    {"role": "user", "content": "What's a must-see in Paris?"},
    {"role": "assistant", "content": "Oh la la! You must visit..."}
  ]
}
```

The training data teaches the model to be enthusiastic about travel!

## Key Insight

> Fine-tuning creates **intrinsic behavior** through examples.  
> Prompt engineering only creates **instructed behavior**.

For consistency and personality, fine-tuning wins.

## Cost Note

Azure resources used in this exercise will incur costs:
- Foundry resource: ~$200-300
- Model deployment: ~$0.50/day
- Fine-tuning: ~$1-2 for this small job

**Always delete resources when done** to avoid unnecessary charges.

## Next Steps

### Want to dive deeper?
→ Read [SETUP.md](SETUP.md) for detailed step-by-step instructions

### Want to see the analysis?
→ Read [FINDINGS.md](FINDINGS.md) for detailed comparison

### Want to see actual responses?
→ Check [results/](results/) folder

## Questions?

Refer to:
- [Microsoft Foundry Docs](https://learn.microsoft.com/foundry)
- [Fine-tuning Guide](https://learn.microsoft.com/foundry/models/fine-tuning)
- Issues/Discussions in this repo

---

**Time to read this**: 5 minutes  
**Time to implement**: 90 minutes  
**Value delivered**: Understanding fine-tuning vs. prompt engineering  

**Ready? Start with [SETUP.md](SETUP.md)!**
