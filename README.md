# MedicalResidencyCodesign

## About this project
This project was developed as a final semester project for MIT's fall 2024 class, 1.S980 (ACT4E, Applied Category Theory for Engineering Design). It uses a codesign framework and MCDPL code to optimally design medical residency programs. We study this problem because today’s residency programs are no longer meeting the needs of a fast-paced, ever-evolving medical landscape. The framework aims to design medical residency within 1 medical specialty and on the timescale of 1 year. 

## Installation/Running the code
To install and run MCDPL locally: follow the instructions in section C (Software Manual) in the Computational Monotone Co-Design book (https://storage.zuper.ai/sync/zupermind/mcdp-book/z7-prod/test/last/test-job/public.pdf)  
   OR  
To use the web-based MCDP editor and solver: 
1. Ask for access to the GitHub organization and repo (contact Gioele Zardini or Yujun Huang)
2. Access the web-editor: https://z7-prod-editor.zuper.ai/editor/
3. Create your own repo in the organization for your project
4. Follow the prompts in the web-editor to get set up

## Problem Setup
At the highest level, this design problem has 4 functionalities and 3 resources.  
Functionalities:
1. Faculty salary
2. Resident salary
3. Quality of resident education
4. Quality of patient care

Resources:
1. Faculty hours/week (the number of hours/week each faculty member works)
2. Resident hours/week (the number of hours/week each resident works)
3. Years to graduate (the number of years of training required to graduate)

This design problem has a feedback loop that takes "number of residents" and "number of patients seen" and returns additional funding to the program. This mimics how hospitals receive funding (primarily from the government) depending on their resident class sizes and how hospitals generate income by seeing/treating patients. 

### Codesign Diagrams
Highest Level Design Problem (DP):
<img width="866" alt="image" src="https://github.com/user-attachments/assets/61414aef-ac39-4723-8e4a-7309710c17c0">

DP divided into smaller, but still overview blocks:
<img width="973" alt="image" src="https://github.com/user-attachments/assets/9ab4b46d-0cd3-41e6-b9cd-2021058f9c77">

Full diagram: 
<img width="942" alt="image" src="https://github.com/user-attachments/assets/09f5d3dd-a59a-450d-b99d-bf600eb3c779">  
To view the entire diagram in more detail please view in the online editor. 

## Known Issues, Assumptions, Limitations, and Possible Future Directions
There are still some problems in the formulation. The resource "years in residency" is meant to constrain how long residents are in school, otherwise, "resident hours/week" goes to zero and "budget" goes to infinity. However, "years in residency" is not currently succeeding at this ("resident hours/week" still goes to zero and "budget" still goes to infinity), so that constraint needs to be looked at again. 

Due to the complexity of medical residencies and medicine as a whole, I have made the following assumptions: 
1. All faculty members and residents are paid the same salary (USD/year not USD/hour)
2. The faculty-student ratio is 4:1 (as required by ACGME)
3. The maximum number of resident hours/week is 80 hours/week (as required by ACGME)
4. Residents work 48 weeks a year
5. There is an "ideal" number of hours necessary to graduate. I set this value at 64800 hours to graduate (135 hrs/week * 48 week/yr * 4 years), which is based on how much residents worked during a 4-year residency program before the 80-hour-per-week regulations.
6. A patient interaction lasts 30 min = 0.5 hour

There were also limitations in the granularity of the functions and models used to describe certain interactions. (We had many "back of the envelope" calculations):
1. We need a better way of quantifying "quality of resident education" and "quality of patient care." In the current model, "quality" is represented as a value between 0 and 1 such that 1 represents 100% of quality potential fulfilled and 0 represents 0% of quality potential fulfilled.  
NOTE: depending on what type of scenario you'd like to model, you can quantify "quality" in many different ways (e.g. patient mortality rate vs patient survey responses vs patient retention rates, etc.)

Other possible factors to consider (that are currently not accounted for in the model):
1. Faculty generally prefer teach patient time instead classroom time because they're paid more for patient hours (and many faculty generally like practical teaching better)
2. This model treats every year of residency as having the same structure (in terms of classroom time and faculty/student ratios). In reality, a 4th year resident should be very close to fully independent - which means that there are fewer faculty resources required for a 4th year resident than a 1st year resident. It is worth noting that if we look at a WHOLE residency program (with 4 graduating classes in the program at any given time - this assumes 4 years to graduation), the resource requirement should be constant across years since the older students and younger student should average each other out.

## Contact
Rita Zambrano - mbcz10@mit.edu  
Project Link: https://github.com/mbcz10/MedicalResidencyCodesign 

## Acknowledgements
Thank you to Professor Gioele Zardini and Yujun Huang for their help with developing and implementing the model. 
