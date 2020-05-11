# kaggle

## Set user credentials
```sh
export KAGGLE_USERNAME=__my_kaggle_username_
export KAGGLE_KEY=__my_kaggle_key_
```

## Clone project
```sh
cd /tmp
git clone https://github.com/kdridi/kaggle.git
cd kaggle
```

## Prepare environment
```sh
python3 -m venv --prompt "kaggle.com" "$(pwd)/.env"
source .env/bin/activate

pip3 install --upgrade pip
pip3 install jupyterlab
```

## Download Kaggle data
```sh
pip3 install kaggle

rm -rf .env/inputs
for challenge in $(cd notebooks; ls -d *); do
	mkdir -p .env/inputs/$challenge
	cd .env/inputs/$challenge
	kaggle competitions download -c $challenge
	unzip $challenge.zip
	rm $challenge.zip
	cd -
done
```

# Install dependencies
```sh
pip3 install pandas
```

# Launch Jupyter
```sh
bash -c "cd notebooks && jupyter-lab --ip=0.0.0.0"
```