# Anaconda

## create env

```sh
conda create -n <env_name> python=<python version> packages
```

## envのエクスポート

* activateした状態で

```sh
conda env export >env.yml
```

## envのインポート

```sh
conda env create --file env.yml
```

* 環境名などはymlに書いてある