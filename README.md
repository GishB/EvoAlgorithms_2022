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
Example of time series which represent uR/h measurment in a drilling well over oil layer
![time_series_change_point_detection](https://user-images.githubusercontent.com/90556084/211688121-49f0e024-e93c-45a4-8cf7-e505c1c41f36.png)

Example of true change points in the measrurment which shows rock types differences between themselves in one well.
![ground_true_labels](https://user-images.githubusercontent.com/90556084/211688473-150ead90-11b8-4bee-99d6-2cbff182c9ac.png)


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


### Final result of hypeparameter selection:
Use eaMuCommaLambda hyperparameter selection for change point detection task and look at this result:
```
best_ind = [21, 28, 12]
F1_score = 0.22
```

![predicted_labels](https://user-images.githubusercontent.com/90556084/211688827-1ed7014a-1d74-4cea-8a4f-ceb1ecf8f32e.png)

The result is TP 47, FP 314, FN 5

## Summary:
- Proceeding from the results of evolutionary algorithms, it has taken into account that between varOr() and varAnd() the first raises the average result of F1 and show less standard deviation of values and results variation between epochs, which makes evolutionary algorithm more robust.

- The population  lambda selection strategy for eaMuCommaLambda shows better result compare to eaMuPlusLambde. For example according to boxplot F1 score distribution  for the first algorithm are higher and robust than for the second one.

Based frameworks: 
 - https://github.com/deap/deap
 - https://github.com/waico/tsad
 - https://github.com/aimclub/Fedot.Industrial
