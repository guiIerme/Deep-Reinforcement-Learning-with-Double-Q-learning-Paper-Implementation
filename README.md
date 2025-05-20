# Deep Reinforcement Learning with Double Q-learning

This repository implements the paper: **[Deep Reinforcement Learning with Double Q-learning](https://arxiv.org/abs/1509.06461)**.

The authors of the paper applied [Double Q-learning](https://papers.nips.cc/paper/3964-double-q-learning) concept on their DQN algorithm. This paper proposed Double DQN, which is similar to DQN but more robust to overestimation of Q-values.

The major difference between those two algorithms is the way to calculate Q-value from target network. Compared to the DQN, directly using Q-value from target network, DDQN chooses an action that maximizes the Q-value of main network at the next state.

## Features

* Employed ***TensorFlow 2*** with performance optimization
* Simple structure
* Easy to reproduce


## How to install

### `virtualenv`

```bash
$ virtualenv venv
$ source venv/bin/activate
$ pip install -r requirements.txt
```

## How to run

You can run Atari 2600 game with `main.py`. Running environment needs to be `NoFrameskip` from `gym` package.

```bash
$ python main.py --help
usage: main.py [-h] [--env ENV] [--train] [--play PLAY]
               [--log_interval LOG_INTERVAL]
               [--save_weight_interval SAVE_WEIGHT_INTERVAL]

Atari: DQN
optional arguments:
  -h, --help            show this help message and exit
  --env ENV             Should be NoFrameskip environment
  --train               Train agent with given environment
  --play PLAY           Play with a given weight directory
  --log_interval LOG_INTERVAL
                        Interval of logging stdout
  --save_weight_interval SAVE_WEIGHT_INTERVAL
                        Interval of saving weights
```

### Example 1: Train BreakoutNoFrameskip-v4

``` bash
$ python main.py --env BreakoutNoFrameskip-v4 --train
```

### Example 2: Play PongNoFrameskip-v4 with trained weights

```bash
$ python main.py --env PongNoFrameskip-v4 --play ./log/[LOGDIR]/weights
```

### Example 3: Control log & save interval

```bash
$ python main.py --env BreakoutNoFrameskip-v4 --train --log_interval 100 --save_weight_interval 1000
```

## Results

This implementation is guaranteed to work well for `Atlantis`, `Boxing`, `Breakout` and `Pong`. Tensorboard summary is located at `./archive`. Tensorboard will show following information:

* Average Q value
* Epsilon (for exploration)
* Latest 100 avg reward (clipped)
* Loss
* Reward (clipped)
* Test score
* Total frames



