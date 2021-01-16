*ShortCut for Pod Logs in K8 (Kubernetes).*

Checking logs of a particular pods generally takes 2 steps and it takes bit time, it needs below 2 commands.

1st is to check the pods id by running command like
kubectl get pods -n <namespace>

2nd is to get the logs using command.
kubectl logs -f <podid> -n <namespace>

We can create a short cut for the above and can create a function, if you put the function in your home directory under file .bashrc file (on linux ~/.bashrc on MAC you can put in ~/.zshrc file), you can use it as command.

pod1() {
kubectl get pods -n <namespace> | awk ‘/<pod name>/{print $1}’ | xargs kubectl logs -f -n <namespace>
}

So next time when you enter pod1 on your tab you will get to see the logs of the pod.
Note : To bring ~/.bashrc (or ~/.zshrc) file change into action, you need to open new tab or new shall and onwards it will start working.

