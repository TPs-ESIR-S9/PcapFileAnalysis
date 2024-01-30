<h1>ESIR-S9 - AI Project : Network Pcap File Analysis</h1>
<b>Yazid BENJAMAA <a href="https://github.com/Xacone">(@Xacone)</a> & Thomas DELAPART <a href="https://github.com/Thomega35">(@Thomega35)</a></b>

(EN CONSTRUCTION)

<h3>Model and input format</h3>

We took the following model from HuggingFace : <a href="https://huggingface.co/rdpahalavan/bert-network-packet-flow-header-payload">rdpahalavan/bert-network-packet-flow-header-payload</a> which classifies a <b>single network packet</b> into one of these categories : 
```
['Analysis', 'Backdoor', 'Bot', 'DDoS', 'DoS', 'DoS GoldenEye', 'DoS Hulk', 'DoS SlowHTTPTest', 'DoS Slowloris', 'Exploits', 'FTP Patator', 'Fuzzers', 'Generic', 'Heartbleed', 'Infiltration', 'Normal', 'Port Scan', 'Reconnaissance', 'SSH Patator', 'Shellcode', 'Web Attack - Brute Force', 'Web Attack - SQL Injection', 'Web Attack - XSS', 'Worms']
```

Each input represents a network packet which respects the following structure :
<br><br>
<img src="img/InputFormat.png">

Pcap files are

<h3>Fine-tuning</h3>

```
TODO:
Ability to train the model with filters
HTTP GET/ File filtering
Removing samples
```

 allow adding training samples to the model 

We can even get rid of

<h3>How to set up the app on Google Collab </h3>

Once executed, the following cell will print a link which will be routing to the app <i>(example : https://twtryxwcltj-496ff2e9c6d22116-5000-colab.googleusercontent.com/) </i> :

```python
from google.colab.output import eval_js
print(eval_js("google.colab.kernel.proxyPort(5000)"))
```

Then execute the next cell that will fire up the backend, it is a flask-based application w/ two endpoints
```python
[....]

@app.route("/")
def home():
    return index

@app.route('/upload', methods=['POST'])
def upload_file():

[...]

if __name__ == "__main__":
    app.run()
[....]
```

Then click the link, you should land on the following app : 

<br><br>

The given notebook allows to use Colab's default GPU w/ Pytorch in order to make trainings/predictions faster :

```python
device = torch.device("cuda:0" if torch.cuda.is_available() else "cpu")
model = model.to(device)
```




