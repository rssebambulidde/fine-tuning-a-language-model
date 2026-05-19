# Fine-Tuning GPT-4.1 for Travel Assistant Chat Application

A hands-on demonstration of fine-tuning a language model with Microsoft Foundry to create a specialized travel assistant with consistent, engaging conversational behavior.

## Project Highlights

- 🚀 **End-to-end AI workflow**: dataset, fine-tuning, deployment, and evaluation
- 🧠 **Technical expertise**: GPT-4.1 fine-tuning, prompt engineering, Azure Foundry
- 📊 **Measurable results**: low loss (0.03), perfect token accuracy, successful deployment
- 📝 **Recruiter-ready documentation**: clear project structure and direct file links

## Project Overview

This project explores the difference between **prompt engineering** and **fine-tuning** by comparing a base GPT-4.1 model with instruction-based guidance to a fine-tuned version trained on curated travel assistant examples.

## Quick Links for Recruiters

- [Project Summary](#project-overview)
- [Skills Demonstrated](#skills-demonstrated)
- [Project Results](#project-results)
- [Setup Guide](SETUP.md)
- [Evaluation & Findings](FINDINGS.md)
- [Training Data](training_data/travel-finetune-hotel.jsonl)
- [Model Responses](results/finetuned_model_responses.md)

### Use Case
Building a travel agency chat application that:
- Suggests destinations and activities
- Maintains consistent, friendly, inspiring tone
- Avoids providing hotel/flight/restaurant bookings
- Asks engaging questions to help users plan trips

## Why This Project is Recruiter-Friendly
- Demonstrates end-to-end AI project execution from dataset preparation to deployment
- Shows ability to compare prompt engineering with fine-tuning and choose the right approach
- Highlights practical experience with Microsoft Foundry and Azure AI model deployment
- Illustrates strong technical writing and clear documentation for non-technical stakeholders

## Skills Demonstrated
- Model fine-tuning with GPT-4.1
- Prompt engineering and behavior design
- Dataset preparation in JSONL format
- Model comparison, evaluation, and analysis
- Azure Foundry deployment and monitoring
- Technical documentation for project delivery

## Key Findings

| Aspect | Base Model + Instructions | Fine-Tuned Model |
|--------|--------------------------|-----------------|
| **Tone** | Informative, generic | Enthusiastic, inspiring |
| **Consistency** | Variable across responses | Consistent personality |
| **Style** | Follows instructions | Embodies trained behavior |
| **Engagement** | Direct recommendations | Engaging questions & exploration |

## What's Included

- **Fine-tuning Job Details**: Configuration, metrics, and training progress
- **Model Comparison**: Side-by-side responses from base vs. fine-tuned models
- **Training Data**: Reference to the JSONL dataset used for fine-tuning
- **Deployment Info**: Model deployment details and access information
- **Results Analysis**: Detailed findings and performance metrics

## Project Files

- [README.md](README.md) — Main project overview and quick summary
- [SETUP.md](SETUP.md) — Step-by-step implementation guide
- [FINDINGS.md](FINDINGS.md) — Detailed analysis and comparison
- [QUICKSTART.md](QUICKSTART.md) — Short fast-start overview
- [PROJECT_STRUCTURE.md](PROJECT_STRUCTURE.md) — File organization and navigation guide
- [CONTRIBUTING.md](CONTRIBUTING.md) — Contribution guidelines
- [LICENSE](LICENSE) — Project license and attribution
- [training_data/travel-finetune-hotel.jsonl](training_data/travel-finetune-hotel.jsonl) — Fine-tuning dataset
- [training_data/training_data_sample.md](training_data/training_data_sample.md) — Training data format examples
- [results/metrics.md](results/metrics.md) — Training metrics and performance report
- [results/base_model_responses.md](results/base_model_responses.md) — Base model test responses
- [results/finetuned_model_responses.md](results/finetuned_model_responses.md) — Fine-tuned model test responses

## Project Results

### Training Metrics
- **Final Train Loss**: 0.03 ✓
- **Token Accuracy**: 1.0 (100%) ✓
- **Training Duration**: 1h 24m
- **Model Version**: gpt-4.1-2025-04-14-ft-1d91a964195a405e8fab42d3fdcb800e-ft-travel

### Deployment Status
- **Status**: Successfully Deployed
- **Deployment Type**: Developer
- **Auto-Deployment**: Enabled

## Getting Started

### Prerequisites
- Azure subscription with Foundry access
- Permissions to create AI resources
- Supported regions: North Central US or Sweden Central

### Steps to Implement

1. **Create Foundry Project**
   - Navigate to https://ai.azure.com
   - Create a new project in a supported region
   - Enable "New Foundry" if not already active

2. **Deploy Base Model**
   - Search for `gpt-4.1` in model catalog
   - Deploy using default settings
   - Test with provided instructions

3. **Prepare Training Data**
   - Download: [travel-finetune-hotel.jsonl](https://microsoftlearning.github.io/mslearn-ai-studio/data/travel-finetune-hotel.jsonl)
   - Ensure .jsonl format (not .txt)

4. **Start Fine-tuning Job**
   - Configuration: See [SETUP.md](SETUP.md)
   - Monitoring: Check progress in Foundry portal

5. **Compare Models**
   - Test both with same queries
   - Evaluate tone, consistency, and engagement

## Quick Test Queries

Test both models with these questions:
- "Where in Rome should I stay?"
- "I'm mostly there for the food. Where should I stay to be within walking distance of affordable restaurants?"
- "What are some local delicacies I should try?"
- "When is the best time of year to visit in terms of the weather?"
- "What's the best way to get around the city?"

## System Instructions Used

```
You are an AI travel assistant that helps people plan their trips. Your objective is to offer 
support for travel-related inquiries, such as visa requirements, weather forecasts, local attractions, 
and cultural norms.
You should not provide any hotel, flight, rental car or restaurant recommendations.
Ask engaging questions to help someone plan their trip and think about what they want to do on their holiday.
```

## File Structure

```
├── README.md                    # This file
├── SETUP.md                     # Detailed setup instructions
├── FINDINGS.md                  # Detailed comparison & analysis
├── results/
│   ├── metrics.json            # Training metrics
│   ├── base_model_responses.md  # Base model test results
│   └── finetuned_model_responses.md  # Fine-tuned model test results
├── training_data/
│   ├── travel-finetune-hotel.jsonl  # Training data (use this file)
│   └── training_data_sample.md      # Training data format explanation
└── images/
    └── screenshots/            # Portal screenshots of results
```

## Time to Complete

- Project setup: 5 minutes
- Base model testing: 10 minutes
- Fine-tuning job: 60-90 minutes (cloud dependent)
- Fine-tuned model testing: 10 minutes
- **Total: ~90 minutes**

## Key Learnings

1. **Fine-tuning teaches behavior** - Training data creates intrinsic conversational patterns
2. **Consistency matters** - Fine-tuned models maintain personality across interactions
3. **Speed vs Quality** - Fine-tuning takes time but delivers superior results
4. **Prompt engineering fallback** - Instructions still valuable for baseline behavior

## Resources

- [Microsoft Foundry Documentation](https://learn.microsoft.com/foundry)
- [Fine-tuning Guide](https://learn.microsoft.com/foundry/models/fine-tuning)
- [GPT-4.1 Model Card](https://learn.microsoft.com/foundry/models/gpt-41)
- [Training Data Format (JSONL)](https://jsonlines.org/)

## Cleanup

Delete Azure resources to avoid costs:
1. Open Azure Portal
2. Navigate to resource group
3. Select "Delete resource group"
4. Confirm deletion

## Author Notes

This project demonstrates the practical value of fine-tuning for specialized applications where consistency and specific behavioral patterns are critical. While prompt engineering provides quick baseline behavior, fine-tuning with curated examples creates models that truly understand your application's unique voice and requirements.

---

**Last Updated**: May 19, 2026  
**Status**: ✓ Project Completed Successfully
