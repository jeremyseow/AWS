# Deployment Options


|Deployment Preference Type|
|------------------------|
|Canary10Percent30Minutes|
|Canary10Percent5Minutes|
|Canary10Percent10Minutes|
|Canary10Percent15Minutes|
|Linear10PercentEvery10Minutes|
|Linear10PercentEvery1Minute|
|Linear10PercentEvery2Minutes|
|Linear10PercentEvery3Minutes|
|AllAtOnce|

- Canary: Traffic is shifted in two increments. You can choose from predefined canary options. The options specify the percentage of traffic that's shifted to your updated Lambda function version in the first increment, and the interval, in minutes, before the remaining traffic is shifted in the second increment.

- Linear: Traffic is shifted in equal increments with an equal number of minutes between each increment. You can choose from predefined linear options that specify the percentage of traffic that's shifted in each increment and the number of minutes between each increment.

- All-at-once: All traffic is shifted from the original Lambda function to the updated Lambda function version at once.