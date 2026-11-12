- Helm use **SemVer*** (Semantic Versioning 2.0.0) track and manage chart releases, dependencies, and Kubernetes version requirements.
- **Chart Version (`version`)**: Defined in `Chart.yaml`, this tracks changes to the Helm chart itself (separate from the actual software version)
- **Application Version (`appVersion`)**: An informal string in `Chart.yaml` showing the version of the containerized application being deployed (does not have to strictly follow SemVer, though the chart version does).
- **Dependency Constraints**: In `Chart.yaml`, you can restrict which sub-chart versions your chart pulls in using SemVer range operators like the caret (`^`) or tilde (`~`):
    - `^1.2.3` allows updates that do not change the left-most non-zero digit (e.g., `>= 1.2.3 < 2.0.0`).
    - `~1.2.3` allows patch-level updates only (e.g., `>= 1.2.3 < 1.3.0`)

---
### Helm upgrade command
- **Automatic Default Behavior:** By default, Kubernetes Deployments use the `RollingUpdate` strategy. When Helm updates a pod template (like changing an image tag), Kubernetes automatically starts spinning up new pods and terminating old ones without any extra flags or manual commands.
- **Configuration Options (Fine-Tuning):** While the rollout is automatic, you can configure _how_ it behaves in your Helm chart's `values.yaml` or Deployment template:
    - **Rollout Speed (`maxSurge` & `maxUnavailable`):** You can control how many extra pods are created at once and how many can be offline during the update.
    - **Strategy Type (`Recreate` vs. `RollingUpdate`):** You can override the default by setting `strategy.type: Recreate` if your app cannot handle running two versions simultaneously. This kills all old pods before starting new ones.
    - **Helm Wait Flag (`--wait`):** By default, `helm upgrade` finishes as soon as it hands the YAML to Kubernetes, even if the pods are still starting up. Adding `--wait` forces Helm to watch the Kubernetes rollout and only mark the upgrade as complete once all new pods are healthy and ready.
    - **Auto-Rollback Flag (`--atomic`):** Adding `--atomic` tells Helm to wait for the rollout and automatically run `helm rollback` if the new pods fail to start within a set timeout.