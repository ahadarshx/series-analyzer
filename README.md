<div align="center">

# series analyzer

**themes, character networks and an in-character chatbot, from a show's subtitles**

<img alt="Python 3.10" src="https://img.shields.io/badge/Python%203.10-b6c4ff?style=flat-square&labelColor=1e1f25&logo=python&logoColor=e3e1e9"> <img alt="spaCy" src="https://img.shields.io/badge/spaCy-dce1ff?style=flat-square&labelColor=1e1f25&logo=spacy&logoColor=e3e1e9"> <img alt="Transformers" src="https://img.shields.io/badge/Transformers-c6c6d0?style=flat-square&labelColor=1e1f25&logo=huggingface&logoColor=e3e1e9"> <img alt="Llama 3 8B" src="https://img.shields.io/badge/Llama%203%208B-b6c4ff?style=flat-square&labelColor=1e1f25&logo=meta&logoColor=e3e1e9"> <img alt="Gradio" src="https://img.shields.io/badge/Gradio-dce1ff?style=flat-square&labelColor=1e1f25&logo=gradio&logoColor=e3e1e9">

![character network](images/relation_canvas.png)

<img alt="themes" src="images/theme_plot.png" width="480">

</div>

## What's in it

Built on Naruto, works with any show that has subtitles.

- **themes**: zero-shot theme scores per episode with `bart-large-mnli`, no training needed
- **character network**: names pulled out with spaCy's transformer NER, drawn as an interactive graph with NetworkX and PyVis
- **jutsu classifier**: a Transformers text classifier trained on jutsu descriptions scraped with Scrapy
- **character chatbot**: talk to Naruto, a Llama 3 8B fine-tuned on his lines
- all four in one Gradio app

## Run

```bash
git clone https://github.com/ahadarshx/series-analyzer.git
cd series-analyzer
pip install -r requirements.txt spacy scrapy
python -m spacy download en_core_web_trf
echo "huggingface_token=hf_..." > .env    # for Llama and the model uploads
python gradio_app.py
```

A GPU is recommended for the classifier and the chatbot. Data sources are in [`data/download_link.txt`](data/download_link.txt).

## Layout

| | |
|---|---|
| `crawler/` | Scrapy spider for the jutsu data |
| `theme_classifier/` | zero-shot theme scoring |
| `character_network/` | NER and the network graph |
| `text_classification/` | the jutsu classifier |
| `character_chatbot/` | the Llama chatbot |

## Credit

Rebuilt and extended from [this tutorial](https://youtu.be/_Hxb1zoY0Qw), for learning. The original idea and guidance are its author's.

<sub>spaCy · Transformers · NetworkX · PyVis · Scrapy · Llama 3 · Gradio</sub>
