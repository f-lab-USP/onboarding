# Túnel remoto de dentro da rede do DOF

## Step 1: log in into the remotehost and start jupyter

On a terminal in your local computer, access woodshole:

    ssh user@woodshole

Now check out your micromamba environment:

    micromamba activate base

And fire up jupyter lab:

    jupyter-lab --no-browser --ip='*' --port=XXXX

where `XXXX` is the port number you'd like to use (e.g., 8889). 


## Step 2: tunnel the jupyterlab service into your localhost
You now need to forward the jupyterlab service, booted up on woodshole through port `XXXX` into port `YYYY`  of your local. You can use `YYYY = XXXX` for simplicity:

    ssh -X -t -t user@woodshole -L XXXX:localhost:YYYY 


## Step 3: open jupyterlab on your localhost

Copy the link generated on the terminal you used to launch jupyter and paste it on your browser. The link resembles: `http://127.0.0.1:9999/lab?token=(...)`.  Et voilà, you have a working jupyterlab running on woodshole that you can iterface with on your local browser.     


# Túnel remoto de fora da rede do DOF


## Step 1: build a tunnel through the firewall server

    ssh -Y -f lab_user@firewall.io.usp.br  -N -L 5522:woodshole:22 

## Step 2: log in into the remotehost and start jupyter

On a terminal in your local computer, access woodshole:

    ssh user@woodshole

Now check out your micromamba environment:

    micromamba activate base

And fire up jupyter lab:

    jupyter-lab --no-browser --ip='*' --port=XXXX

where `XXXX` is the port number you'd like to use (e.g., 8889). 

## Step 3: tunnel the jupyterlab service into your localhost
You now need to forward the jupyterlab service, booted up on woodshole through port `XXXX` into port `YYYY`  of your local. You can use `YYYY = XXXX` for simplicity:

    ssh  -Yp 5522  user@localhost -L YYYY:localhost:XXXX

## Step 4: open jupyterlab on your localhost

Copy the link generated on the terminal you used to launch jupyter and paste it on your browser. The link resembles: `http://127.0.0.1:9999/lab?token=(...)`.  Et voilà, you have a working jupyterlab running on woodshole that you can iterface with on your local browser. 
   