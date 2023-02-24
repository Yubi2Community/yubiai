# Benchmark analysis of Yubi and Other Language Identification Libraries (modified version of [language-identification-survey](https://github.com/modelpredict/language-identification-survey))
Live survey of off-the-shelf language identification tools for python

## Reproducing benchmark

### 1. Download the dataset
```bash
./datasets/tatoeba-sentences-2021-06-05/download
```

### 2. Run the language inference for benchmarks

Available benchmarks:
- fasttext
- fasttext-compressed
- gcld3
- langdetect
- langid
- pycld2
- yulan-e4-v1 aka yubidetect-v1
- yulan-e4-V2 aka yubidetect-v2
- yulan-e8-V2 aka yubidetect-e8-v1

Available datasets:
- tatoeba-sentences-2021-06-05
- tatoeba-sentences-2021-06-05-common-48
- open-subtitles-v2018-100k-per-lang
- yubi_benchmark_dataset_v1
- yubi_benchmark_dataset_v2
- dakshina-dataset-v1 (modified for our usecase.)

On the host machine.
```bash
python run.py <benchmark_name> -d <dataset> -r(optional)
```

In docker:
```bash
docker build -t bench .
docker run -v `pwd`:/src -t -i bench python /src/run.py <benchmark_name> -d <dataset> -r(optional)
```

### 3. Run analysis
```bash
python analyze.py --correctness -d <dataset> -r(optional)
```