# Carbon Tracker


## Setup
Create a virtual environment using `conda` or `virtualenv.` 

```
conda env create --name co2_tracker_env
conda activate co2_tracker_env
pip install . 
```

`co2_tracker` will now be installed to the local environment

#### Online mode (for setups with internet access)

```python
from codecarbon import CarbonTracker
tracker = CarbonTracker()
tracker.start()
# GPU Intensive code goes here
tracker.stop()
```

Or use the decorator

```python
from codecarbon import track_carbon

@track_carbon
def training_loop():
   pass
```
#### Offline mode (for setups without internet access)

The offline tracker can be used as follows:
```python
from codecarbon import OfflineCarbonTracker

tracker = OfflineCarbonTracker(country="Canada")
tracker.start()
# GPU Intensive code goes here
tracker.stop()
```

or 

```python
from codecarbon import track_carbon

@track_carbon(offline=True, country="Canada")
def training_loop():
   pass
```

## Quickstart

For an example application, we use TensorFlow 2.0 on MNIST. 

```
pip install tensorflow
```

Run the examples in `examples/` like so

```
python examples/mnist.py
python examples/mnist_decorator.py
```

## Tests

Make sure `tox` is available

```
pip install tox
```

Run tests by simply entering tox in the terminal when in the root package directory.

```
tox
```

## Generate Documentation
Install [`sphinx.`](https://www.sphinx-doc.org/en/master/usage/installation.html) On MacOS,  
```
brew install sphinx-doc
cd docs
make html
```

## [WIP] Visualization Tool
* Sample data file is in `examples/default.emissions`
* Run with the following command
```
python co2_tracker/viz/co2board.py --filename="examples/default.emissions"
```
