<!-- ---
pretty_name: Bud500
language:
- vi
license:
- cc-by-nc-sa-4.0
multilinguality:
- monolingual
task_categories:
- automatic-speech-recognition
--- -->

# Bud500: A Comprehensive Vietnamese ASR Dataset

Introducing [**Bud500**](https://huggingface.co/datasets/linhtran92/viet_bud500), a diverse Vietnamese speech corpus designed to support ASR research community. With aprroximately **500 hours** of audio, it covers a broad spectrum of topics including podcast, travel, book, food, and so on, while spanning accents from Vietnam's North, South, and Central regions. Derived from free public audio resources, this publicly accessible dataset is designed to significantly enhance the work of developers and researchers in the field of speech recognition.

The corpus was prepared by [**VietAI**](https://vietai.org/) research team, a non-profit organization with the mission of nurturing AI talents and building a community of world-class AI experts in Vietnam.

## Languages

Vietnamese

## Dataset Structure

A typical data point comprises the Audio object dict `audio` and its `transcription`.

```
{'audio': {'path': None,
           'array': array([0.00125122, 0.00228882, 0.00213623, ..., 0.00354004, 0.00442505, 0.00650024]),
           'sampling_rate': 16000},
 'transcription': 'ai cho phép em uống nhiều rượu như vậy'}
```

### Data Fields

- `audio`: A dictionary containing the path to the downloaded audio file, the decoded audio array, and the sampling rate. Note that when accessing the audio column: `dataset[0]["audio"]` the audio file is automatically decoded and resampled to `dataset.features["audio"].sampling_rate`. Decoding and resampling of a large number of audio files might take a significant amount of time. Thus it is important to first query the sample index before the `"audio"` column, _i.e._ `dataset[0]["audio"]` should **always** be preferred over `dataset["audio"][0]`.

- `transcription`: textual form of the audio content.

### Data Splits

The speech material has been subdivided into portions for train, test and validation.

| Total size: 98Gb | Train  | Validation | Test   |
| ---------------- | ------ | ---------- | ------ |
| Samples          | 634158 | 7500       | 7500   |
| Duration         | ~500h  | ~5.46h     | ~5.46h |

### Example usage

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/quocanh34/Bud500/blob/main/examples/load_bud500.ipynb)
[![Open In Huggingface](https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Spaces-blue)](https://huggingface.co/datasets/linhtran92/viet_bud500)

```python
from datasets import load_dataset

auth_token = "Your HuggingFace token"

# Load via Parquet files (~4000 samples in a parquet file)
# Link to other parquet files: https://huggingface.co/datasets/linhtran92/viet_bud500/tree/main/data
train_url = "https://huggingface.co/datasets/linhtran92/viet_bud500/resolve/main/data/train-00000-of-00105-be5f872f8be772f5.parquet"
test_url = "https://huggingface.co/datasets/linhtran92/viet_bud500/resolve/main/data/test-00000-of-00002-531c1d81edb57297.parquet"
data_files = {"train": train_url, "test" : test_url}
dataset = load_dataset("parquet", data_files=data_files, use_auth_token=auth_token, num_proc=2)

# Load via Streaming
dataset = load_dataset("linhtran92/viet_bud500", split='test', streaming=True, use_auth_token=auth_token)

# Load all (649158 samples)
dataset = load_dataset("linhtran92/viet_bud500", split="test", use_auth_token=auth_token, num_proc=2)
```

## Dataset Creation

- Source Data
- Considerations for Using the Data
- Social Impact of Dataset
- Discussion of Biases

## Other Known Limitations

- Dataset provided for research purposes only. Please check dataset license for additional information.

## Dataset Curators

- The dataset was initially prepared by VietAI research team, a non-profit organization with the mission of nurturing AI talents and building a community of world-class AI experts in Vietnam.

## Disclaimer

- During the data collection process, it is possible that some copyrighted material may inadvertently be included. If you believe that your copyrighted material has been included in our dataset without permission, please contact us directly.

## License

```
Copyright (c) 2024 VietAI Research
Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at
    http://www.apache.org/licenses/LICENSE-2.0
Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

## Citation Information

```
@misc{Bud500,
  author = {Anh Pham, Khanh Linh Tran, Linh Nguyen, Thanh Duy Cao, Phuc Phan, Duong A. Nguyen},
  title = {Bud500: A Comprehensive Vietnamese ASR Dataset},
  url = {https://github.com/quocanh34/Bud500},
  year = {2024}
}
```

## Contributors
 
[@quocanh34](https://github.com/quocanh34) [@linhtran6065](https://github.com/linhtran6065) [@linhqyy](https://github.com/linhqyy) [@thanhduycao](https://github.com/thanhduycao) [@pphuc25](https://github.com/pphuc25) [@duongna21](https://github.com/duongna21).

**Please CITE** our repo when it is used to help produce published results or is incorporated into other software.

### Contact

- phamquocanh2002ct@gmail.com
- khanhlinhtran6065@gmail.com
