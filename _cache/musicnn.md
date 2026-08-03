```sh
# On Windows
git clone --depth=1 https://github.com/jordipons/musicnn
cd musicnn
```

```sh
subl requirements.txt
```

```
audioread==3.0.1
librosa==0.8.1
musicnn==0.1.0
numpy==1.16.6
pandas==1.1.5
scikit-learn==0.24.2
scipy==1.5.4
soundfile==0.12.1
tensorflow==2.3.4
resampy==0.2.2
ipython==7.16.3
```

```sh
conda create --name musicnn python=3.6.13
conda activate musicnn
pip install -r requirements.txt
pip install matplotlib
conda install  ipykernel jupyterlab
python -m ipykernel install --user --name musicnn
jupter lab
```