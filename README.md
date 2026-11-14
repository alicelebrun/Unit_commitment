# Unit commitment problem
In this project, I formalize and solve a unit commitment problem involving two kind of production units (thermal plants and reservoir systems) using Pulp/HiGHS.
The objective is to match a daily demand expressed in an hourly basis while miminizing the exploitation cost.

The resulting notebook is here https://github.com/alicelebrun/Unit_commitment/blob/b8327f16f45df9b609d3bd748f014c718a068e74/projet_unit_commitment.ipynb

The output is an animation of the production

<img width="1210" height="757" alt="image" src="https://github.com/user-attachments/assets/110cd34c-70bb-46cd-bfc0-a88d7c018108" />

## Environment

The notebook is written for PuLP 3. PuLP 4 moved its modelling core to Rust and
removed the `cat` argument of `LpVariable`: from version 4 on, binary variables
must be created with `LpProblem.add_variable(..., cat="Binary")`, so the model
has to be ported before it can run with PuLP 4. The versions known to run the
notebook unchanged are listed in `requirements.txt`:

```bash
python -m pip install -r requirements.txt
```

The `HiGHS_CMD` solver is only an interface to the HiGHS executable, which must
be in the `PATH`. Check its availability with:

```python
import pulp
print(pulp.HiGHS_CMD().available())
```

If it prints `False`, install HiGHS (`apt install highs`, or a binary from
https://github.com/ERGO-Code/HiGHS/releases) and check again.
