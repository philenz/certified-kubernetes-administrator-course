- [12-Other-Topics](docs/12-Other-Topics)  
  - [01-Labs-JSON-PATH](docs/12-Other-Topics/01-Labs-JSON-PATH.md)
  - [02-Pre-Requisites-JSON-PATH](docs/12-Other-Topics/02-Pre-Requisites-JSON-PATH.md)
      - https://kodekloud.com/p/json-path-quiz
      - https://mmumshad.github.io/json-path-quiz/index.html#!/?questions=questionskub1
      - https://mmumshad.github.io/json-path-quiz/index.html#!/?questions=questionskub2
      - `$.status.containerStatuses[?(@.name == 'redis-container')].restartCount`
  - [03-Advance-Kubectl-Commands](docs/12-Other-Topics/03-Advance-Kubectl-Commands.md)
      ```bash
      k get nodes -o=jsonpath='{.items[*].metadata.name}'
      
      k config view --kubeconfig=/root/my-kube-config -ojsonpath='{.users[*].name}'
      
      k get pv --sort-by='.spec.capacity.storage'

      k get pv --sort-by='.spec.capacity.storage' -o='custom-columns=NAME:.metadata.name,CAPACITY:.spec.capacity.storage'

      k config view --kubeconfig=my-kube-config -o jsonpath="{.contexts[?(@.context.user=='aws-user')].name}"

      ```
  - [04-Practice-Test-Advance-Kubectl-Commands](docs/12-Other-Topics/04-Practice-Test-Advance-Kubectl-Commands.md)
