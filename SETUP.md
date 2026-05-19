# Setup Instructions - Fine-Tuning GPT-4.1

Complete step-by-step guide to replicate the fine-tuning exercise.

## Prerequisites

✓ Azure subscription with permissions to create AI resources  
✓ Access to Microsoft Foundry (https://ai.azure.com)  
✓ Supported region: North Central US or Sweden Central  

## Step 1: Create Microsoft Foundry Project

1. **Sign In**
   - Open https://ai.azure.com
   - Sign in with your Azure credentials
   - Close any tips or welcome panes

2. **Create Project**
   - Click "Start Building" or navigate to home
   - Select "Create Project" (or "New Project")
   - Enter project name (e.g., `travel-assistant`)

3. **Configure Advanced Options**
   - **Foundry resource**: Accept default (`{project_name}-resource`)
   - **Subscription**: Select your Azure subscription
   - **Resource group**: Create new or select existing
   - **Region**: Select one of:
     - North Central US
     - Sweden Central
   
   ⚠️ These regions are required for gpt-4.1 fine-tuning support

4. **Wait for Project Creation**
   - Provisioning takes 5-10 minutes
   - You'll see the project home page when ready

## Step 2: Deploy Base Model

1. **Access Model Catalog**
   - From project home, select "Find models"
   - Or navigate to "Discover" → "Models" tab

2. **Deploy GPT-4.1**
   - Search for: `gpt-4.1`
   - Review model card
   - Click "Deploy"
   - Use default settings
   - Wait for deployment to complete (~2-3 minutes)

3. **Verify Deployment**
   - Model opens in Playground
   - Ready for testing

## Step 3: Prepare Training Data

1. **Use Project Training Data**
   - This project includes sample training data documentation: [training_data/training_data_sample.md](training_data/training_data_sample.md)
   - This file contains the format explanation and example records you can use
   - For the full production dataset, download from Microsoft Learning:
   ```
   https://microsoftlearning.github.io/mslearn-ai-studio/data/travel-finetune-hotel.jsonl
   ```

2. **Save File**
   - Your device may default to `.txt` extension
   - **Important**: Remove `.txt` suffix to ensure `.jsonl` format
   - Location: Save locally (e.g., `Downloads/travel-finetune-hotel.jsonl`)

3. **Verify Format**
   - Open file in text editor
   - Should see JSONL format (one JSON object per line)
   - Each record contains: `messages` array with system, user, assistant roles

## Step 4: Start Fine-Tuning Job

1. **Navigate to Fine-tune**
   - In Foundry portal left pane, select "Fine-tune"
   - Click blue "Fine-tune" button (upper right)

2. **Configure Fine-tuning Job**
   
   | Setting | Value |
   |---------|-------|
   | Base model | gpt-4.1 |
   | Customization method | Supervised |
   | Training type | Standard |
   | Training data | Upload new dataset → Select `.jsonl` file |
   | Suffix | ft-travel |
   | Auto-deploy | ✓ Checked |
   | Deployment type | Developer |
   | Hyperparameters | Leave defaults |

3. **Submit Job**
   - Click "Submit"
   - ⏱️ **Wait: 60-90 minutes** (cloud dependent)
   - Status visible in Fine-tune pane

4. **Monitor Progress**
   - Select the fine-tuning job
   - View "Monitor" tab for detailed progress
   - Check "Logs" tab for training tasks

## Step 5: Test Base Model (While Fine-tuning Runs)

1. **Open Base Model**
   - Left pane → "Models"
   - Select `gpt-4.1` (base model)

2. **Test 1: No Instructions**
   - Chat prompt: `What can you do?`
   - Observe: Generic response

3. **Update Instructions (First Version)**
   ```
   You are an AI assistant that helps people plan their travel.
   ```
   - Chat prompt: `What can you do?`
   - Observe: Still generic behavior

4. **Update Instructions (Final Version)**
   ```
   You are an AI travel assistant that helps people plan their trips. Your objective is to offer 
   support for travel-related inquiries, such as visa requirements, weather forecasts, local attractions, 
   and cultural norms.
   You should not provide any hotel, flight, rental car or restaurant recommendations.
   Ask engaging questions to help someone plan their trip and think about what they want to do on their holiday.
   ```

5. **Test Query Set**
   Ask and record responses:
   - "Where in Rome should I stay?"
   - "I'm mostly there for the food. Where should I stay to be within walking distance of affordable restaurants?"
   - "What are some local delicacies I should try?"
   - "When is the best time of year to visit in terms of the weather?"
   - "What's the best way to get around the city?"

## Step 6: Test Fine-Tuned Model

1. **Check Fine-tuning Status**
   - Left pane → "Fine-tune"
   - Verify job shows "Completed" ✓
   - If needed, check "Monitor" tab for details

2. **Access Fine-tuned Model**
   - Left pane → "Models"
   - Look for model ending in `-ft-travel`
   - Model name format: `gpt-4.1-2025-04-14-ft-[ID]-ft-travel`
   - Click to open in Playground

   ℹ️ If not listed, select completed fine-tuning job and click "Deploy" manually

3. **Set Instructions**
   - Use same instructions as base model testing:
   ```
   You are an AI travel assistant that helps people plan their trips. Your objective is to offer 
   support for travel-related inquiries, such as visa requirements, weather forecasts, local attractions, 
   and cultural norms.
   You should not provide any hotel, flight, rental car or restaurant recommendations.
   Ask engaging questions to help someone plan their trip and think about what they want to do on their holiday.
   ```

4. **Run Same Query Set**
   - Ask identical test questions
   - Compare responses to base model
   - Note: Tone, consistency, engagement level

5. **Document Comparison**
   - Save/screenshot responses from both models
   - Record observations about differences

## Step 7: Cleanup (Avoid Costs)

1. **Open Azure Portal**
   - https://portal.azure.com

2. **Navigate to Resource Group**
   - Search for resource group created in Step 1
   - Click resource group name

3. **Delete Resources**
   - Click "Delete resource group"
   - Enter resource group name to confirm
   - Click "Delete"
   - ⏱️ Deletion takes 5-10 minutes

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Fine-tuning takes very long | Cloud resources may be busy. Check "Monitor" tab for progress. Be patient (60-90 min is normal) |
| Dataset fails to upload | Ensure file is `.jsonl` not `.txt`. Validate format (one JSON per line). See [training_data/training_data_sample.md](training_data/training_data_sample.md) for format reference |
| Auto-deployment fails | Manually deploy from completed fine-tuning job details page |
| Model not appearing in Models list | Refresh page or wait a few minutes. Check Foundry resource logs if issue persists |
| Region not supported | Ensure you're in North Central US or Sweden Central |

## Performance Expectations

| Metric | Expected | Your Result |
|--------|----------|-------------|
| Final train loss | < 0.1 | |
| Token accuracy | ≥ 0.95 | |
| Training duration | 60-90 min | |
| Fine-tuned model tone | More engaging | |

---

**Documentation**: May 19, 2026  
**Exercise Duration**: ~90 minutes total
