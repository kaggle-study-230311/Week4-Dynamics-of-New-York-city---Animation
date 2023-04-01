# week4-Dynamics-of-New-York-city---Animation

## Object

- predicts the total ride duration of taxi trips in New York City (뉴욕에서 택시 여행의 총 승차 시간을 예측)

## Feature

- **id** - a unique identifier for each trip
- **vendor_id** - a code indicating the provider associated with the trip record (1,2로 구성)
- **pickup_datetime** - date and time when the meter was engaged
- **dropoff_datetime** - date and time when the meter was disengaged
- **passenger_count** - the number of passengers in the vehicle (driver entered value) (0~9로 구성)
- **pickup_longitude** - the longitude where the meter was engaged
- **pickup_latitude** - the latitude where the meter was engaged
- **dropoff_longitude** - the longitude where the meter was disengaged
- **dropoff_latitude** - the latitude where the meter was disengaged
- **store_and_fwd_flag** - This flag indicates whether the trip record was held in vehicle memory before sending to the vendor because the vehicle did not have a connection to the server - Y=store and forward; N=not a store and forward trip (택시기사가 vendor로 전송한 데이터의 주행기록이 차량에 있나없나)(신뢰성 검토 목적??)
- **trip_duration** - duration of the trip in seconds (타깃값)

## How to cluster : KMEANS

### Cluster

- It is the task of grouping a set of objects in such a way that objects in the same group (called a cluster) are more similiar to each other than to those in other groups.
- Popular notions of clusters include groups with small [distances](https://en.wikipedia.org/wiki/Distance_function)
 between cluster members, dense areas of the data space, intervals or particular [statistical distributions](https://en.wikipedia.org/wiki/Statistical_distribution)
- Cluster analysis as such is not an automatic task, but an iterative process of [knowledge discovery](https://en.wikipedia.org/wiki/Knowledge_discovery)
 or interactive multi-objective optimization that involves trial and failure

### KMEANS

- The k-means algorithm divides a set of N samples X into K disjoint clusters C, each decrived mean μ of the samples in the cluster. The means are commonly called “centroids”. **note that they are not points from X, although they live in the same space**
- The K-means algorithm aims to choose centroids that minimise the **inertia(the sum of distances of all points with in a cluster from the centroid of the points)**

\sum_{i=0}^{n}\min_{\mu_j \in C}(||x_i - \mu_j||^2)


[https://scikit-learn.org/stable/modules/clustering.html#k-means](https://scikit-learn.org/stable/modules/clustering.html#k-means)

<aside>
**KMeans**(*n_clusters=8*, ***, *init='k-means++'*, *n_init='warn'*, *max_iter=300*, *tol=0.0001*, *verbose=0*, *random_state=None*, *copy_x=True*, *algorithm='lloyd'*)[[source]](https://github.com/scikit-learn/scikit-learn/blob/9aaed4987/sklearn/cluster/_kmeans.py#L1161)

</aside>

- *n_clusters=8 : The number of clusters (몇개의 centroids을 가져갈지)*
- *n_init='warn' : 몇번 반복진행을 할지*

### parse()

- `parse`함수를 쓰면 자동으로 형식 문자열을 찾아 `datetime` 클래스 객체를 만들어 준다.

EX)`parse('2016-04-16')`

datetime.datetime(2016,4,16,0,0)

### Arrow()

```python
**matplotlib.pyplot.arrow(*x*, *y*, *dx*, *dy*, ***kwargs*)[[source]](https://github.com/matplotlib/matplotlib/blob/v3.7.1/lib/matplotlib/pyplot.py#L2387-L2389)[#](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.arrow.html#matplotlib.pyplot.arrow)**
```

- **x, y**

The x and y coordinates of the arrow base.

- **dx, dy**

The length of the arrow along x and y direction.

### FuncAnimation

```python
matplotlib.animation.FuncAnimation(fig, func, frames=None, init_func=None, fargs=None, 
                                    save_count=None, *, cache_frame_data=True, **kwargs)
```

- fig : 위의 figure
- func : animate함수
- interval: 프레임 사이의 간격을 밀리초 (milliseconds) 단위로 지정

```python
ani.save('animation.gif', writer='imagemagick', fps=2)
```

- save 메서드는 모든프레임을 애니메이션으로 저장
- animation.gif로 저장
