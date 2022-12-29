# EvoAlgorithms_2022
 Homework experiment results for evolutionary course.

dataset available here:
    url = "https://storage.yandexcloud.net/cloud-files-public/dataframe.csv"

Initial parameters:
    epochs = 50
    population_size = 30
    ind_size = 3
    ind_randint_var = [10, 250]
    
 Best F1 score:
 - SimpleEA:
    Best = [135, 31, 14]
    Best fit = 0.22169811320754718
- eaPlusMuLambda:
    Best = [80, 50, 12]
    Best fit = 0.21634615384615385
- eaMuCommaLambda
    Best = [16, 92, 10]
    Best fit = 0.22760290556900728

 Based frameworks: 
 - https://github.com/deap/deap
 - https://github.com/waico/tsad
 - https://github.com/aimclub/Fedot.Industrial
