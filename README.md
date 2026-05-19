# Fine-Tuning GPT-4.1 for Travel Assistant Chat Application

A hands-on project that combines dataset design, model customization, and deployment to build a travel assistant with a consistent, friendly conversational style.

## Project Highlights

- 🚀 **End-to-end AI workflow**: dataset, fine-tuning, deployment, and evaluation
- 🧠 **Technical expertise**: GPT-4.1 fine-tuning, prompt engineering, Azure Foundry
- 📊 **Measurable results**: low loss (0.03), perfect token accuracy, successful deployment
- 📝 **Clear documentation**: all major project content is included in this file for easy review

## What I Built

I fine-tuned GPT-4.1 using travel conversation examples so that the model behaves like a helpful travel assistant. Then I compared it against a prompt-engineered base GPT-4.1 model to show how fine-tuning improves consistency, tone, and engagement.

The project includes:
- Training data preparation in JSONL format
- Fine-tuning a model with Microsoft Foundry
- Deploying the resulting model to a developer endpoint
- Comparing responses from base and fine-tuned models
- Explaining results in plain language for non-technical readers

## Why This Project Matters

This project shows how to move from a general language model to a specialized assistant by teaching the model with examples. It also demonstrates how to:
- choose between prompt engineering and fine-tuning,
- measure performance with simple metrics,
- keep the model aligned with the desired behavior,
- document the process clearly for both technical and non-technical audiences.

## Skills Demonstrated

- Model fine-tuning with GPT-4.1
- Prompt engineering and behavior design
- JSONL dataset preparation
- Model evaluation and comparison
- Azure Foundry deployment and monitoring
- Writing clear, project-focused documentation

## Project Summary: What This File Includes

This README now includes the full content from the other project files:
- the complete setup and implementation steps
- the full findings and analysis
- the easy explanation of technical terms
- the project timeline and results
- the training data information

That means a reader can understand the whole project without leaving this file.

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

### Evaluation Summary

The fine-tuned model delivered responses that were:
- warmer and more engaging,
- more consistent in tone,
- less likely to behave like a generic chatbot,
- better aligned with the travel assistant goal.

## What the Project Does

This project builds a travel planning assistant that:
- answers travel questions in a friendly, helpful tone,
- avoids recommending hotels, flights, car rentals, and restaurants,
- asks follow-up questions to clarify the user's travel preferences,
- gives travel-focused guidance on destinations, weather, culture, and transport.

## Full Implementation Guide

### Prerequisites

Before starting, make sure you have:
- an Azure subscription with permissions to create AI resources,
- access to Microsoft Foundry at https://ai.azure.com,
- a supported region for gpt-4.1 fine-tuning: North Central US or Sweden Central.

### Step 1: Create the Foundry Project

1. Open the Foundry portal at https://ai.azure.com.
2. Sign in with your Azure credentials.
3. Create a new project.
4. In the advanced options, choose a supported region:
   - North Central US
   - Sweden Central
5. Accept the default Foundry resource name or customize it.
6. Select a resource group, or create one.
7. Wait for the project to finish provisioning.

### Step 2: Deploy the Base Model

1. Go to the model catalog in the Foundry portal.
2. Search for `gpt-4.1`.
3. Deploy the model using default settings.
4. Wait for the deployment to complete and open the playground.

### Step 3: Prepare the Training Data

This project includes the dataset file in `training_data/travel-finetune-hotel.jsonl`.

The dataset is in JSONL format, which means:
- each line is one JSON object,
- each object contains a `messages` list,
- each message has a `role` and `content` field.

Example of a single line in JSONL:

```json
{"messages": [{"role":"system","content":"You are an AI travel assistant..."},{"role":"user","content":"What's a must-see in Paris?"},{"role":"assistant","content":"Oh la la! You simply must..."}]}
```

If you download the dataset from the original source, make sure the file is saved with the `.jsonl` extension and not `.txt`.

### Step 4: Start the Fine-Tuning Job

1. In the Foundry portal, open the Fine-tune page.
2. Click the `Fine-tune` button.
3. Configure the job:
   - Base model: `gpt-4.1`
   - Customization method: `Supervised`
   - Training type: `Standard`
   - Training data: upload `travel-finetune-hotel.jsonl`
   - Suffix: `ft-travel`
   - Auto-deploy: enabled
   - Deployment type: `Developer`
4. Submit the job.
5. Monitor progress in the `Monitor` tab.

### Step 5: Test the Base Model

While the fine-tuning runs, test the base GPT-4.1 model with the travel assistant instructions.

Use these directions in the model instructions:

```
You are an AI travel assistant that helps people plan their trips. Your objective is to offer
support for travel-related inquiries, such as visa requirements, weather forecasts, local attractions,
and cultural norms.
You should not provide any hotel, flight, rental car or restaurant recommendations.
Ask engaging questions to help someone plan their trip and think about what they want to do on their holiday.
```

Then try these example queries:
- Where in Rome should I stay?
- I'm mostly there for the food. Where should I stay to be within walking distance of affordable restaurants?
- What are some local delicacies I should try?
- When is the best time of year to visit in terms of the weather?
- What's the best way to get around the city?

### Step 6: Test the Fine-Tuned Model

1. Check the fine-tuning status and wait until it is completed.
2. Open the deployed fine-tuned model.
3. Set the same instructions as the base model.
4. Run the same questions again.
5. Compare the answers for tone, clarity, and consistency.

### Step 7: Clean Up Resources

To avoid unnecessary costs, delete the Azure resource group created for this project:
1. Open the Azure Portal.
2. Find the resource group.
3. Select `Delete resource group`.
4. Confirm the deletion.

## Findings and Analysis

### Training Results

**What happened during training?**
- The model was trained for 10 epochs.
- The training loss decreased from around 4.5 to 0.03.
- The model reached 100% token accuracy on the training data.

**What does that mean?**
- **Loss** measures how far the model's predictions are from the expected output. Lower is better.
- **Token accuracy** measures how often the model predicts the correct next word piece. Higher is better.

### Model Comparison

The base model with instructions was useful, but its behavior changed from answer to answer. The fine-tuned model was more consistent and felt more like a single assistant personality.

#### Example: Rome neighborhood question
- Base model: gave many options and asked for clarification.
- Fine-tuned model: gave a clear recommendation and asked a follow-up question naturally.

#### Example: Food recommendations
- Base model: structured and formal.
- Fine-tuned model: enthusiastic, vivid, and more conversational.

### Why the fine-tuned model was better

Fine-tuning taught the model to adopt the travel assistant style directly. Prompt engineering only gives the model instructions; fine-tuning teaches it how to write those responses consistently.

## Technical Terms Explained

### Fine-tuning
Fine-tuning means training an existing language model on new examples so it learns a new behavior. In this project, fine-tuning teaches the model how to sound like a travel assistant.

### Prompt engineering
Prompt engineering is writing instructions for the base model so it behaves in a desired way. It is useful, but it can be less consistent than fine-tuning.

### JSONL
JSONL is a file format where each line is a separate JSON object. This project uses JSONL to store training examples.

### Training loss
Loss is a number that shows how wrong the model is while learning. Near zero means the model is predicting well on the training data.

### Token accuracy
A token is a small piece of text, like a word or part of a word. Token accuracy measures how often the model predicts the next piece correctly.

### Deployment
Deployment means making the model available to use as a service. In this project, the fine-tuned model was deployed in Azure Foundry as a developer endpoint.

## Training Data

The project includes the training dataset file `training_data/travel-finetune-hotel.jsonl`.

Each training example contains:
- a system message that defines the assistant behavior,
- a user question,
- the assistant's desired response.

This format teaches the model both what to answer and how to answer.

## Simple Results Comparison

| Metric | Base Model | Fine-Tuned Model |
|--------|------------|------------------|
| Tone | Informative | Friendly and engaging |
| Consistency | Variable | Stable across questions |
| Behavior | Instructed | Learned from examples |
| Style | Formal | Natural and conversational |

## Time to Complete

- Project setup: 5 minutes
- Base model testing: 10 minutes
- Fine-tuning job: 60-90 minutes
- Fine-tuned model testing: 10 minutes
- **Total: ~90 minutes**

## Key Learnings

1. Fine-tuning makes behavior more consistent than instructions alone.
2. Good training examples help the model learn tone and personality.
3. Prompt engineering is useful for quick tests, but fine-tuning is better for production behavior.
4. Clear documentation helps non-technical readers understand the project.

## Next Steps

If you want to improve this project further, you can:
- add more diverse travel examples to the training data,
- evaluate the model with real user responses,
- build a simple chat app using the deployed model,
- add a small validation set to measure performance more formally.

## Notes

This README now contains the complete guidance and analysis from the other project files, with technical terms explained in plain language. The remaining markdown files are preserved as backups, but all core project content is available here.

---

**Last Updated**: May 19, 2026  
**Status**: ✓ Project Completed Successfully
