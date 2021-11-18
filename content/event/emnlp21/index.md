---
title: Text privacy presentation for EMNLP 2021

event: EMNLP2021
event_url: https://2021.emnlp.org/

location: Barceló Bávaro Convention Centre
address:
  city: Punta Cana
  country: Dominican Republic

summary: The presentation for our paper CAPE - Context-Aware Private Embeddings for Private Language Learning
abstract: "Neural language models have contributed to state-of-the-art results in a number of downstream applications including sentiment analysis, intent classification and others. However, obtaining text representations or embeddings using these models risks encoding personally identifiable information learned from language and context cues that may lead to privacy leaks. To ameliorate this issue, we propose Context-Aware Private Embeddings (CAPE), a novel approach which combines differential privacy and adversarial learning to preserve privacy during training of embeddings. Specifically, CAPE firstly applies calibrated noise through differential privacy to maintain the privacy of text representations by preserving the encoded semantic links while obscuring sensitive information. Next, CAPE employs an adversarial training regime that obscures identified private variables. Experimental results demonstrate that our proposed approach is more effective in reducing private information leakage than either single intervention, with approximately a 3% reduction in attacker performance compared to the best-performing current method."

# Talk start and end times.
#   End time can optionally be hidden by prefixing the line with `#`.
date: "2021-11-09T13:00:00Z"
#date_end: "2030-06-01T15:00:00Z"
all_day: true

# Schedule page publish date (NOT talk date)
publishDate: "2021-11-09T00:00:00Z"

authors: []
tags: []

# Is this a featured talk? (true/false)
featured: false

image:
  filename: featured.png
  caption: ""
  focal_point: Smart
  preview_only: true

url_code: "https://github.com/RyanGoslingsBugle/priv-text"
url_pdf: "https://aclanthology.org/2021.emnlp-main.628/"
url_slides: "uploads/emnlp_21_poster.pptx"
url_video: "emnlp_21_presentation.mp4"

# Markdown Slides (optional).
#   Associate this talk with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: ""
---
{{< video src="emnlp_21_presentation.mp4" controls="yes" >}}