# AlphaSlice
**Introduction video:**
https://www.youtube.com/watch?v=cJW_EpPYO_Q

⬆️⬆️⬆️⬆️⬆️⬆️⬆️⬆️⬆️⬆️

AI-powered slicer settings and live print monitoring, built to cut 3D printing waste.
AlphaSlice helps makers stop guessing. Import your part, tell the AI what you need, and get slicer settings tuned to the job. Then let a webcam watch the print and stop it early if something goes wrong, so fewer failed prints end up in the trash, reducing waste and saving the climate one print at a time.
<img width="1254" height="1254" alt="image" src="https://github.com/user-attachments/assets/39ede92a-3b41-43da-b700-d6e8f34d0c2d" />


The problem: 
3D printing is more wasteful than people realize
- Settings are guesswork. Picking wall count and infill percentage usually means trial and error. Print, test, adjust, print again. Each failed or over-built attempt burns filament. If you overdo it with the walls, that waste's filament. If theres not enough walls, the entire print breaks in half and is wasted. In the status quo, theres no way to win.
- Failures run to completion. A spaghetti-ed or detached print often keeps going for hours because nobody is watching, wasting even more plastic and energy.

The Solution
AlphaSlice tackles waste at both ends of the print:
- Before printing: AI generates slicer settings (walls, infill, and more) based on your part geometry and your goals for the part, so you get it right the first time.
  
  <img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/9b957236-75fe-4953-a956-c6e2d5b5c977" />
  <img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/4b4664e3-a061-4690-936a-a5feeb7ba570" />


- During printing: A live webcam feed is analyzed with computer vision to detect print issues, then the print is automatically paused or cancelled before more material is wasted.

Features:
1. AI-Generated Slicer Settings
Import your part (e.g. STL) then describe what the part needs to do in plain language (for example, "a wall hook that holds about 5 kg" or "a decorative figurine"). AlphaSlice recommends settings such as wall count and infill matched to your goal, avoiding both under-building and wasteful over-building
<img width="1041" height="475" alt="image" src="https://github.com/user-attachments/assets/efb94ec3-bd44-4946-b7d6-452fdf550c2d" />


3. Live Failure Detection (Vision Ops)
Connects to a webcam pointed at your printer Continuously scans the part while it prints using vision analysis powered by the Groq API for fast inference. Detects issues such as spaghetti, layer shifts, bed detachment, and other visible defects. Automatically pauses or cancels the print when a problem is found and send you a discord message with a live screenshot of the failure.
<img width="1070" height="517" alt="image" src="https://github.com/user-attachments/assets/9072aab8-ca04-476d-8062-59047d9e7cb2" />


4. Built for Sustainability
Less trial-and-error means fewer throwaway prints and less filament per part, early failure detection stops waste the moment it starts.

Impact: 
Across 100 prints of a representative PLA part, AlphaSlice is modeled to cut filament use from 38.0 kg to 23.8 kg, a saving of 14.2 kg (37%). That works out to roughly 151 kWh of energy and 38 kg of CO2e avoided, and 14.2 kg less plastic headed for landfill.

How the numbers were built

<img width="700" height="700" alt="image" src="https://github.com/user-attachments/assets/27a8f906-c257-43c7-875e-9519824db1b9" />


Energy and emissions use 10.6 kWh per kg of printed PLA, 0.207 kg CO2 per kWh (UK grid), and 0.5 kg CO2 per kg of PLA produced.

What is measured and what is modeled
- Failure-side savings are grounded in real data. Obico has logged over 1 million detected failed prints and more than 23,000 kg of filament saved across roughly 90 million monitored hours.
- Settings-side savings are an estimate. The 60% "over-built at defaults" share is an assumption. Measuring actual sliced masses against slicer defaults on a set of real parts would replace this with measured data.

<img width="1596" height="996" alt="image" src="https://github.com/user-attachments/assets/9bc1ede9-9f1c-4607-8911-031ced09089e" />


Sources: 
Song et al., University of Texas at Austin, Material Waste of Commercial FDM Printers Under Realistic Conditions: about 34% of plastic in an open shop was wasted, and failed prints made up about 19% of all material used.
Filamentive, The 3D Printing Waste Problem: failed prints account for over 80% of 3D printing waste, and about 10% of prints become waste.
Petsiuk et al., Synthetic-to-real Composite Semantic Segmentation in Additive Manufacturing: 24% of 5.6 million logged print jobs were canceled.
Pearce group, Open Source Computer Vision-based Layer-wise 3D Printing Analysis: reported failure rates of roughly 1% to 20%.
LLM-3D Print: summarizes studies showing 20% of PLA prints fail and overall failure rates up to 41.1%.
Obico, AI Error Detection in 3D Printing: 89.8 million hours monitored, 1,067,608 failed prints detected, 23,487 kg of filament saved.
QIDI, How Do You Reduce 3D Print Material: a part at 4 walls and 20% infill used about 317 g versus about 159 g at 2 walls and 10% infill.
Forge Labs, Infill Techniques for Making More Efficient FDM Parts: infill optimization can reduce material use by 30 to 70% depending on part function.
Topsbest Precision, 3D Printing Infill Density: Prusa guidance that 10 to 15% infill is often sufficient for general parts.
Enemuoh et al., Energy and Eco-Impact Evaluation of FDM and Injection Molding of PLA: about 50 kWh per kg for FDM of small samples, with about 99% of energy used during the printing phase.
Embodied energy of usable PLA material: 10.6 kWh per kg for the printing step.
Life Cycle Assessment of PLA in 3D Printing Applications: about 0.5 kg CO2 per kg of PLA and a UK grid factor of 0.207 kg CO2 per kWh.
Mechanical Property Characterization of Virgin and Recycled PLA Blends: PLA takes over 80 years to decompose.

What was worked on...
Preparation before hackathon was done, via the ordering of hardware, and the fundamental logics and hardware related changes on Vision OPS.
During the hackathon, Alphaslice was made possible, with advanced and through ai and dataset logical training, and the final incorporation of Vision OPS to bring a greener environment. 
