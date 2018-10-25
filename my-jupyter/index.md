1. jupyter is contained in anaconda. run `jupyter notebook` to run it
2. create new env `conda create -n my-jupyter`

[**change css result in bad interface**install theme adjust css, install vim is not working](https://qiita.com/_snow_narcissus/items/80f81926707807ee9bf1)


[**only in cli** install extension manager, use pip](https://jupyter-contrib-nbextensions.readthedocs.io/en/latest/install.html)

[**not show up on tab** preferred extension manager, use pip](https://github.com/Jupyter-contrib/jupyter_nbextensions_configurator)

### preferred way

```
git clone --depth 1 git@github.com:ipython-contrib/jupyter_contrib_nbextensions.git
cd jupyter_contrib_nbextensions
python setup.py install
#reboot jupyter
```

[install vim plugin](https://github.com/lambdalisue/jupyter-vim-binding/)

## [add jupyter kernel](https://stackoverflow.com/questions/39604271/conda-environments-not-showing-up-in-jupyter-notebook)

```bash
myenv='my-jupyter'
source activate $myenv
python -m ipykernel install --user --name $myenv --display-name "Python ($myenv)"
```

## others problems

[fix module 'pip' has no attribute 'get_installed_distributions](https://www.google.com/search?q=module+%27pip%27+has+no+attribute+%27get_installed_distributions&ie=utf-8&oe=utf-8&client=firefox-b-ab)