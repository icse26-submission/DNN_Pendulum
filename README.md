## CS8395: DNN-based N-Version Repairs

### Preparations

1. Create a conda enviroment:
- Create a new Conda environment with Python 3.11
```conda create -n cartpole python=3.11 -y```

- Activate the environment
```conda activate cartpole```

- Install packages (PyTorch with CUDA 11.8 + others)
```pip install torch==2.0.1+cu118 torchvision==0.15.2+cu118 -f https://download.pytorch.org/whl/torch_stable.html```

- Install the rest of the dependencies
```pip install tqdm==4.66.5 gym==0.26.2 gymnasium==1.1.1 numpy==1.24.3 matplotlib==3.8.0```

2. Download checkpoints
*redacted url*

### Running
1. For training a benign agent:
```
python train.py --seed 16
```

2. For training an attacked agent:
```
python train_attack.py
```

3. For testing an agent:
```
python test_agent.py
```

4. For generating testcases:
```
rm missed_*
rm results.csv
python voter.py
python generate_testcases.py
```

5. For fine-tuning an agent:

```python
python repair.py --fim_reg 10 --mixed_ratio 0.2 --repair_mode fail_only
```

Repair mode can chosen from: ["fail_only", "mixed", "fim","masked", "unlearn"]. The default ratio of pass/total test cases used are 0.2.

