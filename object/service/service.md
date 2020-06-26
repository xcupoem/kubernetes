###完整的Service
```
apiVersion: v1            # 必须 string
kind: Service             # 必须 string
metadata:                 # 必须 obj
  name: string            # 必须,service名称，须符合RFC1035规范 string
  namespace: string       # 必须，默认default； string
  labels:                 # 自定义标签属性列表list
    - name: string
  annotations:            # 注释 自定义 list
    - name: string
spec:                     # 必须 详细描述obj
  selector:               # 必须 list label selector 配置，将选择具有指定label标签的Pod作为管理范围
  #key: volume            # 必须,作用与带有指定标签的Pod
  type: string            # 必须 string service 类型，指定访问service方式，默认ClusterIP,NodePort,LoadBalancer
  externalTrafficPolicy: Local #Cluster或者Local,Cluster(默认)表示：流量可以转发到其他节点上的Pod，性能损失一丢丢,Local表示：流量只发给本机的Pod，性能好性能好一丢丢
  clusterIP: string       # spec.type=LoadBalancer 需指定
  sessionAffinity: string # 是否支持session,默认空，可选值为ClientIP：表示将同一个客户端（根据客户端IP地址决定）的访问请求都转发到同一个后端Pod
  ports:
  - name: string          # 端口名称
    protocol: string      # 端口协议，支持TCP和UDP；默认TCP
    port: int             # 供集群中其它服务访问的端口（服务监听端口号）,一般port 和 targetPort一致
    targetPort: int       # 需要转发到后端Pod的端口号（后端Pod中container暴露的端口），,相当于Dockerfile中的EXPOSE
    nodePort: int         # 当spec.type=NodePort时，指定映射到物理机的端口
  status:                 # obj 当spec.type=LoadBalancer时，设置外部均衡器的地址，用于共有云环境
    loadBalancer:         # obj 外部负载均衡器
      ingress:            # obj 外部负载均衡器
        ip: string        # 外部负载均衡器IP地址 
        hostname: string  # 外部负载均衡器的主机名

```
