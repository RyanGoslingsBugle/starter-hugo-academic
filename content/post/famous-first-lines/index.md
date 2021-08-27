---
title: Famous first lines with VQGan + CLIP
subtitle: Can we learn something about a novel by generating images?

# Summary for listings and search engines
summary: We use VQGan+CLIP to generate images from the famous first lines of novels. Can you spot some thematic markers in the output?

# Link this post with a project
projects: []

# Date published
date: "2021-08-08T00:00:00Z"

# Date updated
lastmod: ""

# Is this an unpublished draft?
draft: false

# Show this page in the Featured widget?
featured: false

# Featured image
# Place an image named `featured.jpg/png` in this page's folder and customize its options here.
image:
  caption: ""
  focal_point: ""
  placement: 2
  preview_only: false

authors:
- admin

tags:
- generation
- machine_learning
- deep_learning

# categories:
# - Demo
# - 教程
---

Text-to-Image generation is a curious field that, aside from producing a [vast array of monstrosities](https://www.aiweirdness.com/), can also provide some insight into the visual conceptual embeddings inherent in social language. We can even exploit that social linguistic programming to reproduce some conceptual information that is associated with entities even when they aren't fully contained in the input prompt.

To explore this idea, I've generated a list of famous opening lines from novels, ideas about which might be embedded in in the language corpus used to trained text-to-visual representation learning systems—after all, how many essays have posted online about 1984 that analyse the sentence "It was a bright cold day in April and the clocks were striking thirteen". How many of those have some relationship to visual concepts that we would link to the book's themes of state control, linguistic determinism, and the abscence of free will?

My intuition was that for the most famous of these cultural entities, a naive text-to-image generation process based on first lines alone should demonstrate at least some qualities we associate with the novel. Thankfully, adapting existing code for such a system is pretty straightforward since there are plenty of implementations online. 

Check out:

* [olaviinha/NeuralTextToImage](https://github.com/olaviinha/NeuralTextToImage)
* [kcosta42/VQGAN-CLIP-Docker](https://github.com/kcosta42/VQGAN-CLIP-Docker)
* [nerdyrodent/VQGAN-CLIP](https://github.com/nerdyrodent/VQGAN-CLIP)

The solution I adapted for local generation was initially created by [Katherine Crowson](https://github.com/crowsonkb). You can check out the original notebook in Colab: [![Open In Colab][colab-badge]][colab-notebook]

[colab-notebook]: <https://colab.research.google.com/drive/1L8oL-vLJXVcRzCFbPwOoMkPKJ8-aYdPN>
[colab-badge]: <https://colab.research.google.com/assets/colab-badge.svg>

My solution, which you can easily adapt to any set of prompts by switching out the input CSV, can be found at [ryangoslingsbugle/VQGan_CLIP](https://github.com/RyanGoslingsBugle/VQGan_CLIP).


Samples
======
<div style="display:flex; flex-wrap: wrap;">
      <img src="https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/herzog/progress_1000.png" alt="Herzog" style="max-width: 50%; padding:5px;" /> 
      <img src="https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/voyage_of_the_dawn_treader/progress_1000.png" alt="Voyage of the Dawn Treader" style="max-width: 50%; padding:5px;" />
      <img src="https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_crow_road/progress_1000.png" alt="The Crow Road" style="max-width: 50%; padding:5px;" />
      <img src="https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/neuromancer/progress_1000.png" alt="Neuromancer" style="max-width: 50%; padding:5px;" />
</div>


Method
======

CLIP
-----

[CLIP](https://openai.com/blog/clip/) is a supervised natural language learning model trained to classify images and optimised for maximum transfer potential across benchmark datasets. The idea is that not training for best performance on a single dataset will produce more robust outcomes, better suited to out-of-training-domain flexibility.

OpenAI have adopted a simple approach to producing transferable visual models with their CLIP network. This system follows the general process of masked language model learning, learning to predict which caption applies to which image, essentially producing a kind of visual concept embedding.

Read more in [Radford, et al. (2021)](https://arxiv.org/abs/2103.00020).

```
@misc{radford2021learning,
      title={Learning Transferable Visual Models From Natural Language Supervision}, 
      author={Alec Radford and Jong Wook Kim and Chris Hallacy and Aditya Ramesh and Gabriel Goh and Sandhini Agarwal and Girish Sastry and Amanda Askell and Pamela Mishkin and Jack Clark and Gretchen Krueger and Ilya Sutskever},
      year={2021},
      eprint={2103.00020},
      archivePrefix={arXiv},
      primaryClass={cs.CV}
}
```

VQGan
-----

VQGan is a combination of a convolutional representation generator with an auto-regressive transformer for reconstruction. This setup achieves extremely good results in image reconstruction tasks, and loading pre-trained models makes working with with it quite straightforward.

Read more in [Esser, et al. (2020)](https://arxiv.org/abs/2012.09841).

```
@misc{esser2021taming,
      title={Taming Transformers for High-Resolution Image Synthesis}, 
      author={Patrick Esser and Robin Rombach and Björn Ommer},
      year={2021},
      eprint={2012.09841},
      archivePrefix={arXiv},
      primaryClass={cs.CV}
}
```


Outputs
======
Below you can see the full set of novels chosen, the input text used, and the image generated after the 1000th training epoch.

| Title | Text | Image |
|---|---|---|
| A Tale of Two Cities | "It was the best of times, it was the worst of times" | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/a_tale_of_two_cities/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/a_tale_of_two_cities/progress_1000.png ) |
| 1984 | It was a bright cold day in April and the clocks were striking thirteen. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/1984/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/1984/progress_1000.png) |
| Fahrenheit 451 | It was a pleasure to burn. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/fahrenheit_451/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/fahrenheit_451/progress_1000.png) |
| Anna Karenina | Happy families are all alike; every unhappy family is unhappy in its own way. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/anna_karenina/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/anna_karenina/progress_1000.png) |
| Pride and Prejudice | It is a truth universally acknowledged that a single man in possession of a good fortune must be in want of a wife. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/pride_and_prejudice/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/pride_and_prejudice/progress_1000.png) |
| Moby Dick | Call me Ishmael. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/moby_dick/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/moby_dick/progress_1000.png) |
| The Hobbit | In a hole in the ground there lived a hobbit. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_hobbit/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_hobbit/progress_1000.png) |
| Slaughterhouse Five | "All this happened, more or less." | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/slaughterhouse_five/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/slaughterhouse_five/progress_1000.png) |
| The Metamorphosis | As Gregor Samsa awoke one morning from uneasy dreams he found himself transformed in his bed into a gigantic insect. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_metamorphosis/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_metamorphosis/progress_1000.png) |
| Voyage of the Dawn Treader | "There was a boy called Eustace Clarence Scrubb, and he almost deserved it." | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/voyage_of_the_dawn_treader/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/voyage_of_the_dawn_treader/progress_1000.png) |
| The Great Gatsby | In my younger and more vulnerable years my father gave me some advice | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_great_gatsby/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_great_gatsby/progress_1000.png) |
| The Go-Between | The past is a foreign country; they do things differently there. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_go-between/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_go-between/progress_1000.png) |
| The Crow Road | It was the day my grandmother exploded. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_crow_road/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_crow_road/progress_1000.png) |
| The Bell Jar | "It was a queer, sultry summer, the summer they electrocuted the Rosenbergs, and I didn't know what I was doing in New York." | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_bell_jar/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_bell_jar/progress_1000.png) |
| To Kill a Mockingbird | "When he was nearly thirteen, my brother Jem got his arm badly broken at the elbow." | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/to_kill_a_mockingbird/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/to_kill_a_mockingbird/progress_1000.png) |
| Invisible Man | I am an invisible man. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/invisible_man/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/invisible_man/progress_1000.png) |
| One Hundred Years of Solitude | Colonel Aureliano Buendía was to remember that distant afternoon when his father took him to discover ice. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/one_hundred_years_of_solitude/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/one_hundred_years_of_solitude/progress_1000.png) |
| Don Quixote | Somewhere in la Mancha a gentleman lived not long ago one of those who has a lance and ancient shield on a shelf and keeps a skinny nag and a greyhound for racing. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/don_quixote/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/don_quixote/progress_1000.png) |
| Scaramouche | He was born with a gift of laughter and a sense that the world was mad. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/scaramouche/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/scaramouche/progress_1000.png) |
| The Trial | "Someone must have slandered Josef K., for one morning, without having done anything truly wrong, he was arrested." | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_trial/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_trial/progress_1000.png) |
| The Stranger | Mother died today. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_stranger/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_stranger/progress_1000.png) |
| The Old Man and the Sea | He was an old man who fished alone in a skiff in the Gulf Stream and he had gone eighty-four days now without taking a fish. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_old_man_and_the_sea/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_old_man_and_the_sea/progress_1000.png) |
| The Middle Passage | "Of all the things that drive men to sea, the most common disaster, I've come to learn, is women." | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_middle_passage/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_middle_passage/progress_1000.png) |
| Neuromancer | "The sky above the port was the color of television, tuned to a dead channel." | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/neuromancer/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/neuromancer/progress_1000.png) |
| A Frolic of His Own | "Justice? You get justice in the next world, in this world you have the law." | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/a_frolic_of_his_own/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/a_frolic_of_his_own/progress_1000.png) |
| Paradise | They shoot the white girl first. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/paradise/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/paradise/progress_1000.png) |
| Notes From the Underground | I am a sick man... I am a spiteful man. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/notes_from_the_underground/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/notes_from_the_underground/progress_1000.png) |
| A Clockwork Orange | "There was me, that is Alex, and my three droogs and we sat in the Korova milkbar trying to make up our rassoodocks what to do with the evening." | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/a_clockwork_orange/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/a_clockwork_orange/progress_1000.png) |
| Chromos | "The moment one learns English, complications set in." | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/chromos/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/chromos/progress_1000.png) |
| Back When We Were Grownups | "Once upon a time, there was a woman who discovered she had turned into the wrong person." | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/back_when_we_were_grownups/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/back_when_we_were_grownups/progress_1000.png) |
| The Dark Tower | The man in black fled across the desert and the gunslinger followed. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_dark_tower/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_dark_tower/progress_1000.png) |
| The End of the Affair | A story has no beginning or end; arbitrarily one chooses that moment of experience from which to look back or from which to look ahead. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_end_of_the_affair/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_end_of_the_affair/progress_1000.png) |
| Their Eyes Were Watching God | Ships at a distance have every man's wish on board. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/their_eyes_were_watching_god/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/their_eyes_were_watching_god/progress_1000.png) |
| Catch-22 | It was love at first sight. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/catch-22/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/catch-22/progress_1000.png) |
| I Capture the Castle | I write this sitting in the kitchen sink. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/i_capture_the_castle/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/i_capture_the_castle/progress_1000.png) |
| Ethan Frome | "I had the story, bit by bit, from various people, and, as generally happens in such cases, each time it was a different story." | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/ethan_frome/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/ethan_frome/progress_1000.png) |
| City of Glass | "It was a wrong number that started it, the telephone ringing three times in the dead of night, and the voice on the other end asking for someone he was not." | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/city_of_glass/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/city_of_glass/progress_1000.png) |
| The Red Badge of Courage | "The cold passed reluctantly from the earth, and the retiring fogs revealed an army stretched out on the hills, resting." | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_red_badge_of_courage/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_red_badge_of_courage/progress_1000.png) |
| Tracks | "We started dying before the snow, and like the snow, we continued to fall." | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/tracks/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/tracks/progress_1000.png) |
| Tristram Shandy | I begin with writing the first sentence - and trusting to Almighty God for the second. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/tristram_shandy/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/tristram_shandy/progress_1000.png) |
| The Napoleon of Notting Hill | The human race has been playing at children's games from the beginning and will probably do it till the end | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_napoleon_of_notting_hill/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_napoleon_of_notting_hill/progress_1000.png) |
| Murphy | "The sun shone, having no alternative, on the nothing new." | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/murphy/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/murphy/progress_1000.png) |
| Waiting | "Every summer Lin Kong returned to Goose Village to divorce his wife, Shuyu." | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/waiting/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/waiting/progress_1000.png) |
| The Tin Drum | "Granted, I am an inmate of a mental hospital; my keeper is watching me, he never lets me out of his sight" | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_tin_drum/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_tin_drum/progress_1000.png) |
| Changing Places | "High, high above the North Pole, on the first day of 1969, two professors of English Literature approached each other" | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/changing_places/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/changing_places/progress_1000.png) |
| Herzog | "If I am out of my mind, it's all right with me, thought Moses Herzog." | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/herzog/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/herzog/progress_1000.png) |
| Gravity's Rainbow | A screaming comes across the sky. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/gravity's_rainbow/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/gravity's_rainbow/progress_1000.png) |
| The Third Man | One never knows when the blow may fall. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_third_man/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_third_man/progress_1000.png) |
| The Satanic Verses | "To be born again, sang Gibreel Farishta tumbling from the heavens, first you have to die." | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_satanic_verses/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_satanic_verses/progress_1000.png) |
| Middlemarch | Miss Brooke had that kind of beauty which seems to be thrown into relief by poor dress. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/middlemarch/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/middlemarch/progress_1000.png) |
| Cat's Eye | "Time is not a line but a dimension, like the dimensions of space." | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/cats_eye/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/cats_eye/progress_1000.png) |
| The Silmarillion | "There was Eru, the One, who in Arda is called Ilúvatar; and he made first the Ainur, the Holy Ones, that were the offspring of his thought" | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_silmarillion/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_silmarillion/progress_1000.png) |
| Wide Sargasso Sea | "They say when trouble comes close ranks, and so the white people did." | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/wide_sargasso_sea/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/wide_sargasso_sea/progress_1000.png) |
| Crash | Vaughan died yesterday in his last car-crash. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/crash/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/crash/progress_1000.png) |
| The Sound and the Fury | "Through the fence, between the curling flower spaces, I could see them hitting." | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_sound_and_the_fury/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_sound_and_the_fury/progress_1000.png) |
| A Portrait of the Artist as a Young Man | Once upon a time and a very good time it was there was a moocow coming down along the road | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/a_portrait_of_the_artist_as_a_young_man/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/a_portrait_of_the_artist_as_a_young_man/progress_1000.png) |
| Elmer Gantry | Elmer Gantry was drunk. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/elmer_gantry/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/elmer_gantry/progress_1000.png) |
| Blown Away | Psychics can see the color of time it's blue. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/blown_away/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/blown_away/progress_1000.png) |
| Pale Fire | I was the shadow of the waxwing slain By the false azure in the windowpane | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/pale_fire/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/pale_fire/progress_1000.png) |
| Mrs Dalloway | Mrs. Dalloway said she would buy the flowers herself. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/mrs_dalloway/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/mrs_dalloway/progress_1000.png) |
| A Farewell to Arms | In the late summer of that year we lived in a house in a village that looked across the river and the plain to the mountains. | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/a_farewell_to_arms/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/a_farewell_to_arms/progress_1000.png) |
| The Towers of Trebizond | "Take my camel, dear, said my Aunt Dot, as she climbed down from this animal on her return from High Mass." | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_towers_of_trebizond/progress_1000.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/the_towers_of_trebizond/progress_1000.png) |
| Riddley Walker | On my naming day when I come 12 I gone front spear and kilt a wyld boar he parbly ben the las wyld pig on the Bundel Downs | [![](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/riddley_walker/progress_100.png)](https://raw.githubusercontent.com/RyanGoslingsBugle/VQGan_CLIP/master/output/riddley_walker/progress_100.png) |