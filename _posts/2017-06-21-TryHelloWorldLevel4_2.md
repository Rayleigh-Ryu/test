---
layout: post
title: "TryHelloWorld Level4 (2)"
description: "TryHelloWorld Level4 (2)"
date: 2017-06-21
tags: [Algorithm, python]
comments: true
---

#### 02. 공항 건설하기

> 1보다 큰 N개의 도시 중 한 곳에 공항을 지을 예정입니다. 사람들의 편의를 위해 공항으로부터 각 사람들까지의 도시간 이동 거리가 최소가 되는 도시에 짓기로 하였습니다. 편의상 도시는 일직선상에 놓여있다고 가정하며 **좌표의 범위는 음수가 포함**됩니다. 또한 좌표는 정렬되어 있지 않습니다. 직선상의 위치와 그 도시에 사는 사람들의 수가 주어질 때, 공항을 지을 도시의 위치를 반환해주는 함수 chooseCity 함수를 완성하세요. 거리가 같은 도시가 2개 이상일 경우 위치가 더 작은 쪽의 도시를 선택하면 됩니다. 예를 들어 다음과 같은 정보의 도시가 있다고 가정해 봅시다.
>
> |  위치  |  1   |  2   |  3   |
> | :--: | :--: | :--: | :--: |
> | 인구수  |  5   |  2   |  3   |
>
> 이 살 경우, 각각의 도시에 공항을 지었을 때의 사람들의 이동 거리는 **8, 8, 12** 이므로 1번 또는 2번에 지을 수 있지만, **1의 위치가 더 작으므로** 1을 반환해주면 됩니다

```python
def chooseCity(n,city):
    city.sort(key=lambda x: x[0])
    total = sum([x[1] for x in city])
    s = 0
    for i in range(n):
        s += city[i][1]
        if s >= (total // 2): 
            break
    return city[i][0]
```

- 문제의 이해가 필요하다.
- 우선 도시의 위치와 그 도시의 인구가 한 쌍으로 데이터가 들어온다. 우리는 각 도시의 위치에 따른 상대적인 거리를 구하는 것이므로 이 위치에 따라서 1차적으로 정렬을 해준다.`city.sort(key=lambda x:x[0])`
- 이제 정렬된 위치에서 각 도시의 상대적인 거리를 구해야하는데 역시나 가장 쉽게 생각해볼수 있는 방법은 도시 하나를 기준으로 잡고 그 외의 모든 도시에 대한 상대이동거리가 가장 작은 것을 구하는 방법이다.
- 하지만 저 방식은 역시나 시간 오버가 뜬다.
- 그래서 생각해본 방법이 모든 도시의 인구수를 구한다음 평균을 구해서 이 평균이랑 가장 차이가 많이나는 것이 가장 효율적인 위치지 않을까라는 생각을 하였다.
- 하지만 이럴 경우 아웃라이어 값이 존재하면 맞는 답이 나오질 않았다.
- 그래서 다시 생각한 방법이 평균에 집착하여 자신의 좌측의 값이 전체 인구수의 절반이 넘어가면 좌우로의 이동의 평균 지점이 되므로 가장 효율적인 위치가 아닐까하여 생각한 방식이 위의 코드이다.









































