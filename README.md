# AlphaSlice
AI-powered slicer settings and live print monitoring, built to cut 3D printing waste.
AlphaSlice helps makers stop guessing. Import your part, tell the AI what you need, and get slicer settings tuned to the job. Then let a webcam watch the print and stop it early if something goes wrong, so fewer failed prints end up in the trash, reducing waste and saving the climate one print at a time.

The problem: 
3D printing is more wasteful than people realize
- Settings are guesswork. Picking wall count and infill percentage usually means trial and error. Print, test, adjust, print again. Each failed or over-built attempt burns filament. If you overdo it with the walls, that waste's filament. If theres not enough walls, the entire print breaks in half and is wasted. In the status quo, theres no way to win.
- Failures run to completion. A spaghetti-ed or detached print often keeps going for hours because nobody is watching, wasting even more plastic and energy.

The Solution
AlphaSlice tackles waste at both ends of the print:
- Before printing: AI generates slicer settings (walls, infill, and more) based on your part geometry and your goals for the part, so you get it right the first time.
- During printing: A live webcam feed is analyzed with computer vision to detect print issues, then the print is automatically paused or cancelled before more material is wasted.

Features:
1. AI-Generated Slicer Settings
Import your part (e.g. STL) then describe what the part needs to do in plain language (for example, "a wall hook that holds about 5 kg" or "a decorative figurine"). AlphaSlice recommends settings such as wall count and infill matched to your goal, avoiding both under-building and wasteful over-building

2. Live Failure Detection (Vision Ops)
Connects to a webcam pointed at your printer Continuously scans the part while it prints using vision analysis powered by the Groq API for fast inference. Detects issues such as spaghetti, layer shifts, bed detachment, and other visible defects. Automatically pauses or cancels the print when a problem is found and send you a discord message with a live screenshot of the failure.

3. Built for Sustainability
Less trial-and-error means fewer throwaway prints and less filament per part, early failure detection stops waste the moment it starts.

Impact: 

Show Image

Across 100 prints of a representative PLA part, AlphaSlice is modeled to cut filament use from 38.0 kg to 23.8 kg, a saving of 14.2 kg (37%). That works out to roughly 151 kWh of energy and 38 kg of CO2e avoided, and 14.2 kg less plastic headed for landfill.

How the numbers were built
<img width="1082" height="1084" alt="image" src="https://github.com/user-attachments/assets/27a8f906-c257-43c7-875e-9519824db1b9" />


Energy and emissions use 10.6 kWh per kg of printed PLA, 0.207 kg CO2 per kWh (UK grid), and 0.5 kg CO2 per kg of PLA produced.

What is measured and what is modeled
- Failure-side savings are grounded in real data. Obico has logged over 1 million detected failed prints and more than 23,000 kg of filament saved across roughly 90 million monitored hours.
- Settings-side savings are an estimate. The 60% "over-built at defaults" share is an assumption. Measuring actual sliced masses against slicer defaults on a set of real parts would replace this with measured data.

<?xml version="1.0" encoding="UTF-8"?>
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 900 600" width="900" height="600" role="img" aria-labelledby="t d" font-family="Helvetica, Arial, sans-serif" xmlns:c2pa="http://c2pa.org/manifest"><metadata><c2pa:manifest>AAAWgmp1bWIAAAAeanVtZGMycGEAEQAQgAAAqgA4m3EDYzJwYQAAABZcanVtYgAAAEdqdW1kYzJtYQARABCAAACqADibcQN1cm46YzJwYTo5MjVmMGU5Ny02NTEzLTRlNjQtOGE0Yy0xNDliY2ViYzExMjIAAAADl2p1bWIAAAApanVtZGMyYXMAEQAQgAAAqgA4m3EDYzJwYS5hc3NlcnRpb25zAAAAALxqdW1iAAAARGp1bWRjYm9yABEAEIAAAKoAOJtxE2MycGEuaW5ncmVkaWVudC52MwAAAAAYYzJzaDc2V+tlICoejZharQqsT4QAAABwY2JvcqNpZGM6Zm9ybWF0bWltYWdlL3N2Zyt4bWxqaW5zdGFuY2VJRHgseG1wOmlpZDpkMDE1MzEwYS0zMTJjLTQ3YzgtYjczYi1lMDk5NDJlMDgzZDNscmVsYXRpb25zaGlwaHBhcmVudE9mAAAB4mp1bWIAAABBanVtZGNib3IAEQAQgAAAqgA4m3ETYzJwYS5hY3Rpb25zLnYyAAAAABhjMnNoFoVnIEW0GSr/Z7LPplOYzgAAAZljYm9yomdhY3Rpb25zgqJmYWN0aW9ua2MycGEub3BlbmVkanBhcmFtZXRlcnOha2luZ3JlZGllbnRzgaJjdXJseC1zZWxmI2p1bWJmPWMycGEuYXNzZXJ0aW9ucy9jMnBhLmluZ3JlZGllbnQudjNkaGFzaFggg6HeAlb4aQiZSchXDslng16MFFsRKf/+SgGqGFNyHk6kZmFjdGlvbngdY29tLmFudGhyb3BpYy5jbGF1ZGUucHJvdmlkZWRqcGFyYW1ldGVyc6F4H2NvbS5hbnRocm9waWMub3JpZ2luLWNvbmZpZGVuY2VndW5rbm93bmtkZXNjcmlwdGlvbnhmQ2xhdWRlIHByb3ZpZGVkIHRoaXMgZmlsZSBhdCB0aGUgcmVxdWVzdCBvZiBhIHVzZXIgYW5kIG1heSBoYXZlIGNyZWF0ZWQgb3IgbW9kaWZpZWQgdGhlIGZpbGUgY29udGVudHMubXNvZnR3YXJlQWdlbnShZG5hbWVmQ2xhdWRlcmFsbEFjdGlvbnNJbmNsdWRlZPUAAADIanVtYgAAAEBqdW1kY2JvcgARABCAAACqADibcRNjMnBhLmhhc2guZGF0YQAAAAAYYzJzaIhcUEezEJQep0ufEOJ2+rQAAACAY2JvcqVjYWxnZnNoYTI1NmNwYWRMAAAAAAAAAAAAAAAAZGhhc2hYII6xEIJL663s5khsh35xSdcUGBHapjHPLUGqfLPErSx3ZG5hbWVuanVtYmYgbWFuaWZlc3RqZXhjbHVzaW9uc4GiZXN0YXJ0GQEJZmxlbmd0aBkeBAAAAj5qdW1iAAAAJ2p1bWRjMmNsABEAEIAAAKoAOJtxA2MycGEuY2xhaW0udjIAAAACD2Nib3KlY2FsZ2ZzaGEyNTZpc2lnbmF0dXJleE1zZWxmI2p1bWJmPS9jMnBhL3VybjpjMnBhOjkyNWYwZTk3LTY1MTMtNGU2NC04YTRjLTE0OWJjZWJjMTEyMi9jMnBhLnNpZ25hdHVyZWppbnN0YW5jZUlEeCx4bXA6aWlkOjE3MjJmZWI1LTg1OWQtNDI1OS1hZGYzLWJmYWRkMjc5MmNmZXJjcmVhdGVkX2Fzc2VydGlvbnODomN1cmx4LXNlbGYjanVtYmY9YzJwYS5hc3NlcnRpb25zL2MycGEuaW5ncmVkaWVudC52M2RoYXNoWCCDod4CVvhpCJlJyFcOyWeDXowUWxEp//5KAaoYU3IeTqJjdXJseCpzZWxmI2p1bWJmPWMycGEuYXNzZXJ0aW9ucy9jMnBhLmFjdGlvbnMudjJkaGFzaFggaKyhj6XmiXRotWh+JpdF7t5L7Wka+v8EulhGTGJqQgmiY3VybHgpc2VsZiNqdW1iZj1jMnBhLmFzc2VydGlvbnMvYzJwYS5oYXNoLmRhdGFkaGFzaFggGpWfZowpcy5RrbR+i9P2Zln3yoUFK5zXhTpV1oZu4Xx0Y2xhaW1fZ2VuZXJhdG9yX2luZm+jZG5hbWVvQW50aHJvcGljIEZpbGVzZ3ZlcnNpb25lMS4wLjBrc3BlY1ZlcnNpb25lMi40LjAAABA4anVtYgAAAChqdW1kYzJjcwARABCAAACqADibcQNjMnBhLnNpZ25hdHVyZQAAABAIY2JvctKEWQISogEmGCFZAgowggIGMIIBjaADAgECAhRA5aAK7sI50L64g/oGQgU9Z1UTADAKBggqhkjOPQQDAzBJMRcwFQYDVQQKEw5BbnRocm9waWMsIFBCQzEuMCwGA1UEAxMlQW50aHJvcGljIENvbnRlbnQgQ3JlZGVudGlhbHMgUm9vdCBDQTAeFw0yNjA4MDcxODQzNTZaFw0yODA4MDYxOTQzNTZaMEQxFzAVBgNVBAoTDkFudGhyb3BpYywgUEJDMSkwJwYDVQQDEyBBbnRocm9waWMgQ2xhdWRlIENvbnRlbnQgU2lnbmluZzBZMBMGByqGSM49AgEGCCqGSM49AwEHA0IABJh6CmvLUBgFFNU0vUKlOVtE6djd17L5SuwX0LemFisBM3dkd/3cyjxFA3Qo5S46fX0/ihY0VZ7mfb9KF703t5OjWDBWMA4GA1UdDwEB/wQEAwIHgDAVBgNVHSUEDjAMBgorBgEEAYPoXgIBMAwGA1UdEwEB/wQCMAAwHwYDVR0jBBgwFoAUzlHiBIFOZFsj+OPEz5o+nMHXXMIwCgYIKoZIzj0EAwMDZwAwZAIwMXMdFJ4BetLLVY7ORuE9noqbbAZOZn/aArXyTwFAZfKrPzxF2vPoJNf1+UCdg1XGAjBwX1zd9WGqYkqmL5SFqw1QySjr1zJfpJM9+1rdDwSPLMOPOjKuiXjoU/pUUeG9RwmhY3BhZFkNngAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAPZYQKs7yUkXYJnaUGooirDDh94rQElZpLcPhG6Y2u8EVCxMMD4Mf6EG1H7nAXmi4gCwlDH121hB7Zf6Vnu/97IYrhw=</c2pa:manifest></metadata>
  <title id="t">Filament use per 100 prints, with and without AlphaSlice</title>
  <desc id="d">Stacked bar chart. Without AlphaSlice: 31.7 kg in finished parts plus 6.3 kg lost to failed prints, 38.0 kg total. With AlphaSlice: 22.2 kg in finished parts plus 1.6 kg lost to failed prints, 23.8 kg total. Saving of 14.2 kg, or 37 percent.</desc>
  <defs>
    <marker id="arr" viewBox="0 0 10 10" refX="5" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse">
      <path d="M0,0 L10,5 L0,10 z" fill="#0f7a55"/>
    </marker>
  </defs>

  <rect x="0.5" y="0.5" width="899" height="599" rx="12" fill="#ffffff" stroke="#e1e0d9"/>

  <text x="40" y="44" font-size="22" font-weight="600" fill="#0b0b0b">Filament use per 100 prints</text>
  <text x="40" y="68" font-size="13" fill="#52514e">Modeled estimate for a representative PLA part. Assumptions are listed in the README.</text>

  <rect x="40" y="90" width="12" height="12" rx="2" fill="#2a78d6"/>
  <text x="60" y="101" font-size="13" fill="#52514e">Material in finished parts</text>
  <rect x="250" y="90" width="12" height="12" rx="2" fill="#eb6834"/>
  <text x="270" y="101" font-size="13" fill="#52514e">Material lost to failed prints</text>

  <g stroke="#e1e0d9" stroke-width="1">
    <line x1="110" y1="130" x2="600" y2="130"/>
    <line x1="110" y1="210" x2="600" y2="210"/>
    <line x1="110" y1="290" x2="600" y2="290"/>
    <line x1="110" y1="370" x2="600" y2="370"/>
  </g>
  <line x1="110" y1="450" x2="600" y2="450" stroke="#c3c2b7" stroke-width="1"/>
  <g font-size="12" fill="#898781" text-anchor="end">
    <text x="100" y="134">40 kg</text>
    <text x="100" y="214">30 kg</text>
    <text x="100" y="294">20 kg</text>
    <text x="100" y="374">10 kg</text>
    <text x="100" y="454">0</text>
  </g>

  <rect x="170" y="196.4" width="160" height="253.6" fill="#2a78d6"/>
  <rect x="170" y="146" width="160" height="50.4" fill="#eb6834"/>
  <rect x="170" y="196.4" width="160" height="2" fill="#ffffff"/>

  <rect x="430" y="272.4" width="160" height="177.6" fill="#2a78d6"/>
  <rect x="430" y="259.6" width="160" height="12.8" fill="#eb6834"/>
  <rect x="430" y="272.4" width="160" height="2" fill="#ffffff"/>

  <g font-size="14" font-weight="500" fill="#ffffff" text-anchor="middle">
    <text x="250" y="328">31.7 kg</text>
    <text x="250" y="176">6.3 kg</text>
    <text x="510" y="365">22.2 kg</text>
  </g>
  <text x="422" y="270" font-size="12" font-weight="500" fill="#b8481d" text-anchor="end">1.6 kg lost</text>

  <g font-size="16" font-weight="600" fill="#0b0b0b" text-anchor="middle">
    <text x="250" y="136">38.0 kg</text>
    <text x="510" y="249">23.8 kg</text>
  </g>

  <g stroke="#52514e" stroke-width="1" stroke-dasharray="4 3">
    <line x1="334" y1="146" x2="640" y2="146"/>
    <line x1="594" y1="259.6" x2="640" y2="259.6"/>
  </g>
  <line x1="625" y1="148" x2="625" y2="257.6" stroke="#0f7a55" stroke-width="2" marker-start="url(#arr)" marker-end="url(#arr)"/>
  <text x="642" y="198" font-size="18" font-weight="600" fill="#0f7a55">&#8722;14.2 kg</text>
  <text x="642" y="220" font-size="14" font-weight="500" fill="#0f7a55">&#8722;37%</text>

  <g font-size="14" font-weight="500" fill="#0b0b0b" text-anchor="middle">
    <text x="250" y="474">Without AlphaSlice</text>
    <text x="510" y="474">With AlphaSlice</text>
  </g>

  <g>
    <rect x="40" y="500" width="190" height="74" rx="8" fill="#f4f3ee"/>
    <text x="54" y="522" font-size="12" fill="#52514e">Filament saved</text>
    <text x="54" y="551" font-size="24" font-weight="600" fill="#0b0b0b">14.2 kg</text>
    <text x="54" y="566" font-size="11" fill="#52514e">37% less per 100 prints</text>

    <rect x="250" y="500" width="190" height="74" rx="8" fill="#f4f3ee"/>
    <text x="264" y="522" font-size="12" fill="#52514e">Energy avoided</text>
    <text x="264" y="551" font-size="24" font-weight="600" fill="#0b0b0b">151 kWh</text>
    <text x="264" y="566" font-size="11" fill="#52514e">at 10.6 kWh per kg</text>

    <rect x="460" y="500" width="190" height="74" rx="8" fill="#f4f3ee"/>
    <text x="474" y="522" font-size="12" fill="#52514e">CO2e avoided</text>
    <text x="474" y="551" font-size="24" font-weight="600" fill="#0b0b0b">38 kg</text>
    <text x="474" y="566" font-size="11" fill="#52514e">grid power + PLA production</text>

    <rect x="670" y="500" width="190" height="74" rx="8" fill="#f4f3ee"/>
    <text x="684" y="522" font-size="12" fill="#52514e">Landfill plastic avoided</text>
    <text x="684" y="551" font-size="24" font-weight="600" fill="#0b0b0b">14.2 kg</text>
    <text x="684" y="566" font-size="11" fill="#52514e">PLA persists 80+ years</text>
  </g>
</svg>

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

