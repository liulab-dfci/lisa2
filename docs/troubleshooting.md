# Troubleshooting data downloading

Occasionally, a user may not be able to connect to cistrome.org from their institutional server due to some security measure. To circumvent this, one can manually install the data required to run LISA. 

First, on the server, use the command below to issue the download URL for the required dataset.

*server*
```bash
$ lisa download hg38 oneshot --url
http://cistrome.org/~alynch/data/lisa_data/hg38_1000_2.0.h5
```

This example fetches the URL for downloading the data to run the "oneshot" command with human genes. 

Copy this URL, then on your local machine, download LISA's required data from cistrome.org.

*local*
```bash
$ wget http://cistrome.org/~alynch/data/lisa_data/hg38_1000_2.0.h5
```

Now, transfer the downloaded LISA data from your local machine to your working directory on the server:

*local*
```bash
$ scp ./hg38_1000_2.0.h5 {user}@{server}:/{PATH_TO_DIR}/
```

Once the data is has transferred, the last step is to install the data in the server package and install it to LISA's package directory:

*server*
```bash
(lisa_env) $ lisa install hg38 oneshot ./hg38_1000_2.0.h5 --remove
```

The LISA site package folder should now contain a directory called ```data``` with the downloaded dataset inside:
```
data/
├── hg38_1000_2.0.h5
```
