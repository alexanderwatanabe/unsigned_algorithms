# unsigned_algorithms
On-chain NFT project on Cardano

Click the Binder button below to open up an interactive Python/Jupyterlab instance to run the code in this repository, after it loads, double-click "unsig_gen.ipynb" on the left.

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/alexanderwatanabe/unsigned_algorithms/HEAD?urlpath=lab)

## Easy

1. Go to https://www.unsigs.com/details/##### (replace ###### with the 5 digit number, including leading zeros, of your unsig)

2. Type the properties you see on your unsig's page, into the notebook unsig_gen.ipynb - if you don't want to make a mistake, copy the portion between the square brackets ( "[" and "]" ) for each property, into the notebook. 

## Medium

### Getting metadata:

1. Go to https://cardanoscan.io and paste the transaction (something like 91363703c99b14c6f980b19d435b9f78a9cee6f98c1ff9be5e5e4cc3ba44ee6b) where you received your unsigs into the search box.

2. Click the "Metadata" tab

3. Click the "{ }" text below the "Value" entry, this has the metadata of the minting transaction of your transaction, if you bought in an early phase, there may be multiple unsigs in a single mint transaction. In that case, you need to look for the unsig##### that matches the unsig you are looking for.

4. There are multiple KEY:VALUE pairs in this metadata. A KEY is kind of like an address or name, and the VALUE is what is stored at that address. 

5. You should see something like what is shown below:

            unsigs: {
                        index: 17429,
                        num_props: 5,
                        properties: {
                           colors: [
                              "Red",
                              "Green",
                              "Blue",
                              "Green",
                              "Blue"
                           ],
                           distributions: [
                              "CDF",
                              "CDF",
                              "CDF",
                              "CDF",
                              "CDF"
                           ],
                           multipliers: [
                              "0.5",
                              "1",
                              "1",
                              "2",
                              "4"
                           ],
                           rotations: [
                              "0",
                              "270",
                              "180",
                              "180",
                              "90"
                           ]
                        }
                     }

You need to copy the part AFTER "unsigs: " from the first "{" to the corresponding "}" at the end (there are 2 right after each other, the first one closes the "{" after the properties KEY).

6. Paste that into the unsig_gen.ipynb notebook in this repository, after the "unsig = " statement
7. You will need to add quotes around the KEYS (the words: index, num_props, properties, colors, distributions, multipliers and rotations) due to differences between how the metadata is recorded on Cardano and what Python expects.
8. You will need to remove quotes around the numbers in the lists of multipliers and rotations (in the example above 0.5, 1, 1, 2, 4 and 0, 270, 180, 180, 90

### Bonus time (just for your info)

7. The code for unsig_gen.ipynb is stored on Cardano, in our genesis unsig00000: you can see this in the metadata under the key "source_tx_id". Try copying the value stored at source_tx_id into cardanoscan.io.

8. Traverse over the metadata in that transaction, following the keys listed in your unsig under "source_key" ("721", genesis_tx_id, "unsig00000", "files", "code") to find the code that is in the notebook provided for you. This code, and the accompanying environment file, are sufficient to recreate your unsigs from almost any computer.


## Hard

Compile and run an instance of cardano-node and cardano-db-sync, query the raw node data for your transaction over postgresql. If you know how to do this you don't need this guide :D
