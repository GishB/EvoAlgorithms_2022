# EvoAlgorithms_2022
 Experiment results for hyperparameter selection in change point detection module in Fedot.Industrial framework.
 - Evolutionary algorithm based on deap framework.
 - Evoluation function based on SingularSpectrumTransformation class from Fedot.Industrial framework.
 - Score function based on TSAD framework.

Dataset loading:
```
    url = "https://storage.yandexcloud.net/cloud-files-public/dataframe.csv"
    df = pd.read_csv(StringIO(requests.get(url).content.decode('utf-8')), sep='|')
```

Initial parameters:
```
    epochs = 50
    population_size = 30
    ind_size = 3
    ind_randint_var = [10, 250]
```
    
 Best hypeparameters / F1 score:
 - SimpleEA:
 ```
    Best = [135, 31, 14]
    Best fit = 0.221
```
- eaPlusMuLambda:
```
    Best = [80, 50, 12]
    Best fit = 0.216
```
- eaMuCommaLambda
```
    Best = [16, 92, 10]
    Best fit = 0.227
```

 Based frameworks: 
 - https://github.com/deap/deap
 - https://github.com/waico/tsad
 - https://github.com/aimclub/Fedot.Industrial
