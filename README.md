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
![eaSimple](https://user-images.githubusercontent.com/90556084/211684540-1174e3ca-0137-4755-8116-1fd24c8fe68e.png)
```
    Best = [135, 31, 14]
    Best fit = 0.22
```
- eaPlusMuLambda:

![eaMuPlusLambda](https://user-images.githubusercontent.com/90556084/211684834-1e5ab681-9836-44ff-b3ba-9e411d347bf0.png)
```
    Best = [80, 50, 12]
    Best fit = 0.21
```
- eaMuCommaLambda

![EaMuCommaLambda__DEAP_Samofalov_2022](https://user-images.githubusercontent.com/90556084/211685032-5fc149ee-8d4c-4a76-bc3a-86ae32214d2f.png)
```
    Best = [16, 92, 10]
    Best fit = 0.22
```

In addition 10 times run has been done for each evolutionary algorithms. There is next key hypeparameters:
```
    number_iterations = 10
    generations = 10
    pop_size = 10
    ind_size = 3
    ind_example = [250, 50, 25]
```

![загруженное](https://user-images.githubusercontent.com/90556084/211684115-20ce6e52-b4f4-4c0c-8104-61377703ee99.png)


| Name | Average pop result | The best ind result | epochs | iterations |
| --- | --- | --- | --- | --- |
| SimpleEA | 0.16 | 0.21 | 10 | 10 |
| eaMuPlusLambda | 0.19 | 0.21 | 10 | 10 |
| eaMuCommaLambda | 0.19 | 0.22 | 10 | 10 |



## Summary:
- Proceeding from the results of evolutionary algorithms, it has taken into account that between varOr() and varAnd() the first raises the average result of F1 and show less standard deviation of values and results variation between epochs, which makes evolutionary algorithm more robust.

- The population  lambda selection strategy for eaMuCommaLambda shows better result compare to eaMuPlusLambde. For example according to boxplot F1 score distribution  for the first algorithm are higher and robust than for the second one.


Based frameworks: 
 - https://github.com/deap/deap
 - https://github.com/waico/tsad
 - https://github.com/aimclub/Fedot.Industrial
