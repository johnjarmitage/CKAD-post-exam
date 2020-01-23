## Notes after sitting CKAD certification exam

* 19 questions with marks that vary from 15% to 2%, but the majority of questions have a mark of between 8 and 5%. The mark does not correspond to the level of difficulty.
* There are four clusters, and you are told which one to use at the beginning of each question.
* Do not expect to be able to answer all questions in 120 minutes. Leave the questions worth < 3% to the end, and return to them only if you have the time.
* Check if the question tells you to work in a certain namespace.
* Work fast but be precise.

#### Sorts of questions
The questions range from relatively short ones, as in the list of questions found in the dgkanatsios github repo [CKAD-exercises](https://github.com/dgkanatsios/CKAD-exercises), to the longer questions found in the Linux Academy course.

The questions cover all of the topics touched on within the Linux Academy course. Get comfortable with creating pods, deployments, jobs, cronjobs, and services. There will also be rolling updates and rollbacks. Network policies will be in there along with everything else touched on in the Linux Academy course. If you don't know then of course there are the docs to search, but this can be time consuming and stressful, so best to know the maximum.

#### Tips
 
 I would recommend that you are comfortable with writing YAML files fast in `vim`. Get used to the commands such as `d` (tap twice) to delete a line, then `i` to insert text, `ESC` then `:x` to save and quit. You don't want to waist time with `nano`.
 
 I sat the exam with a linux environment. This allowed me to use the middle button on the mouse to paste text. This is faster that using unfamiliar methods proposed for copy and paste, because ctrl+C and ctrl+V does not work.
 
 The exam environment is self explanatory and not worth worrying about. Questions are on the left and a terminal session is on the right. You can have another tab open with the kubernetes doc. 
 
 Clear the desk of everything, and have no notes on the walls.
 
 Breath, you have time...
 
 #### Tricks

Add auto-completion before you begin:
```
source <(kubectl completion bash)
```

To avoid writing YAML from scratch get used to the following commands:

* Create a YAML for editing for a pod called `my-pod`, for example in a namespace `test`, with an `nginx` image exposed on port `80`:
```
kubectl run my-pod --image=nginx --restart=Never --port=80 -n test --dry-run -o yaml > my-pod.yml
```
* Create the same but as a deployment (see the table on flags in the [docs](https://kubernetes.io/docs/reference/kubectl/conventions/) to understand more):
```
kubectl run my-pod --image=nginx --port=80 -n test --dry-run -o yaml > my-pod.yml
```
* Use the help function to get hints for commands you can't quite remember before giving up and going to look for them in the docs. For example `cronjob`:
```
kubectl create cronjob --help
```
* To get the base YAML for a service:
```
kubectl expose my-svc deploy my-deploy --port=80 --target-port=8080 --dry-run -o yaml > my-svc.yml
```
* To hunt for errors when debugging, don't waist time searching each namespace and each object:
```
kubectl get all --all-namespaces
```
* Don't panic, read the error messages when your `kubectl create` does not work.

#### Resources I used

https://kubernetes.io/docs/reference/kubectl/cheatsheet/

https://github.com/dgkanatsios/CKAD-exercises

https://gist.github.com/veggiemonk/70d95df77029b3ebe58637d89ef83b6b

#### P.S.

I hope I don't have to do it again.

