## Step 1: log in into the remotehost and start jupyter

On a terminal in your local computer, access woodshole:

    $ ssh user@woodshole

Now check out your micromamba environment:

    $ micromamba activate base

And fire up jupyter lab:

    $ jupyter-lab --no-browser --ip='*' --port=XXXX

where `XXXX` is the port number you'd like to use (e.g., 8889). 


## Step 2: tunnel the jupyterlab service into your localhost
You now need to forward the jupyterlab service, booted up on woodshole through port `XXXX` into port `YYYY`  of your local. You can use `YYYY = XXXX` for simplicity:

    $ ssh -X -t -t user@woodshole -L XXXX:localhost:YYYY 


## Step 3: open jupyterlab on your localhost

Go to your browser and type `localhost:XXXX`.  Et voilà, you have a working jupyterlab running on woodshole that you can iterface with on your local browser. 
    

