### Data Statement
Our model relied on the OPUS-100 dataset, a collection of publicly available parallel texts
mapped from English to other languages, for training. The dataset, curated by the University of
Helsinki, has scraped sources such as government documents, movie subtitles, and news articles in
many languages, pairing different translations of the same text together. For example, OPUS pairs a
sentence from an English Wikipedia article with the corresponding sentence in its French translation.
While the dataset features 99 language pairs (from English to another language), we utilized only 13
distinct languages for training. These languages are English (en), Chinese (zh), Japanese (ja), Hindi
(hi), Russian (ru), Arabic (ar), Bengali (bn), French (fr), Spanish (es), Italian (it), Portuguese (pt),
Turkish (tr), Korean (ko), Hebrew (he). We chose these languages because of their global popularity
and diversity, allowing our model to work with the most frequently spoken languages and the world.
