Mining Litecoin Silver
===

### Download the miner
* sources from [nheqminer](https://github.com/litecoinsilver/nheqminer)
```bash
	git clone https://github.com/litecoinsilver/nheqminer
```

### Install from sources
Build from the sources
```bash
	cd nheqminer/nheqminer
	cmake .
	make
	sudo make install
```

### Run
Run nheqminer with the following options:
* -l : stratum proxy url 
* -u : ltcsilver address / worker
* -p : password ( if specify a ltcsilver address use password "x")
* -t : number of threads
```bash
	nheqminer -l pool.lts.chickenkiller.com:3857 -u YourBitcoinAdress.YourWorker -p x -t threadCount
```
Runnable example:
```bash
	nheqminer -l pool.lts.chickenkiller.com:3857 -u mwao1nfAjX6KAsHVQ7e1e8sjRjMKB4HsXb -p x -t 1
```
