```
  990  cd 18-Taint-and-Toleration/
  991  ls
  992  cat helloworld.yaml
  993  ls
  994  cp -rf ../05-Deployments/helloworld.yaml .
  995  ls
  996  kubectl apply -f helloworld.yaml
  997  kubectl  get pods
  998  kubectl  get pods -o wide
  999  ls
 1000  kubectl  get pods -o wide
 1001  kubectl  get nodes
 1002  kubectl taint node worker2 app=myapp:NoSchedule
 1003  kubectl  describe node worker2 | grep -i taint
 1004  kubectl  get pods
 1005  kubectl  get pods -o wide
 1006  kubectl scale --replicas=10 deploy helloworld-deployment
 1007  kubectl  get pods -o wide
 1008  kubectl scale --replicas=1 deploy helloworld-deployment
 1009  kubectl  get pods -o wide
 1010  kubectl scale --replicas=5 deploy helloworld-deployment
 1011  kubectl  get pods -o wide
 1012  ls
 1013  kubectl  get pods
 1014  kubectl  get pods -o wide
 1015  kubectl scale --replicas=3 deploy helloworld-deployment
 1016  ls
 1017  mv helloworld.yaml 01-helloworld.yaml
 1018  mv helloworld-toleration.yaml 02-helloworld-toleration.yaml
 1019  ls -ltr
 1020  vim 02-helloworld-toleration.yaml
 1021  ls
 1022  kubectl delete -f 01-helloworld.yaml
 1023  kubectl apply -f 02-helloworld-toleration.yaml
 1024  kubectl  get pods -o wide
 1025  cat 01-helloworld.yaml
 1026  cat 02-helloworld-toleration.yaml
 1027  ls
 1028  mv helloworld-toleration-2.yaml 03-helloworld-toleration-2.yaml
 1029  vim 03-helloworld-toleration-2.yaml
 1030  ls
 1031  kubectl  delete -f 02-helloworld-toleration.yaml
 1032  ls
 1033  kubectl  delete -f helloworld-ds.yaml
 1034  ls
 1035  kubectl  get pods
 1036  ls
 1037  cat 03-helloworld-toleration-2.yaml
 1038  kubectl taint node worker2 app=example:NoSchedule
 1039  kubectl taint node worker2 example=amit:NoSchedule
 1040  kubectl describe nodes | grep -i taint
 1041  kubectl describe nodes worker2 | grep -i taint
 1042  kubectl describe nodes worker2 | grep -A10 taint
 1043  kubectl describe nodes worker2 | grep -A 10 taint
 1044  kubectl describe nodes worker2 | grep -iA10 taint
 1045  ls
 1046  kubectl  apply -f 02-helloworld-toleration.yaml
 1047  kubectl  get pods -o wide
 1048  kubectl describe nodes worker2 | grep -iA5 taint
 1049  vim 03-helloworld-toleration-2.yaml
 1050  ls
 1051  kubectl  apply -f 03-helloworld-toleration-2.yaml
 1052  kubectl  get pods
 1053  kubectl  get pods -o wide
 1054  ls
 1055  mv helloworld-toleration-3.yaml 04-helloworld-toleration-3.yaml
 1056  vim 04-helloworld-toleration-3.yaml
 1057  ls
 1058  kubectl  apply -f 04-helloworld-toleration-3.yaml
 1059  kubectl  get pods
 1060  kubectl  get pods -o wide
 1061  ls
 1062  cat 04-helloworld-toleration-3.yaml
 1063  kubectl taint node worker1 example2=example2-key:NoExecute
 1064  ls
 1065  mv helloworld-ds.yaml 05-helloworld-ds.yaml
 1066  cat 05-helloworld-ds.yaml
 1067  kubectl  describe node master | grep -i taint
 1068  kubectl  apply -f 05-helloworld-ds.yaml
 1069  kubectl  describe node | grep -i taint
 1070  kubectl taint node worker2 app-
 1071  kubectl taint node worker1 example2-
 1072  kubectl  describe node | grep -i taint
 1073  kubectl taint node worker2 example-
 1074  ls
 1075  cd ..
 1076  kubectl  delete -f 18-Taint-and-Toleration/

```
