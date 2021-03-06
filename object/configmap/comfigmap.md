### configmap示例
<pre>
以下两种configmap创建方式也可以写在一起，即configmap可以一次性的定义多个文件和普通变量  

apiVersion: v1
kind: ConfigMap
metadata:
  namespace: poem
  name: line-config
data:
  # key 和 value均为字符串
  key1: value1
  key2: value2

---
apiVersion: v1
kind: ConfigMap
metadata:
  namespace: poem
  name: line-config2
data:
  # key 和 value均为字符串
  line-config.yaml
    key1:
      key11: value11
    key2: value2    

### 引用方式
1. 环境变量方式
env:
- name: key1 # 此时key1的值为value1
  valueFrom:
    configMapKeyRef:
      name: line-config
      key: key1
envFrom:
- configMapRef:
  name: line-config
2. volume方式
    volumeMounts:
    - name: v1
      mountPath: /etc/config #此处会生成一个文件/etc/config/line-config.yaml，文件名称极为key的名字
volumes:
- name: v1
  configMap:
    name: line-config2
    
---
volumes:
  - name: v2
  configMap:
    name: line-config2
    items:
    - key: line-config.yaml
      path: line-config.yaml
</pre>