## Description

This test creates a policy that enforces the restricted profile and a policy exception that exempts any pod whose image is `nginx` in the `staging-ns` namespace and sets the `allowPrivilegeEscalation` field.

## Steps

1.  - Create a cluster policy
    - Assert the policy becomes ready
1.  - Create a policy exception for the cluster policy created above.
1.  - Try to create a pod named `good-pod-1` with `allowPrivilegeEscalation` set to `false` in the `default` namespace, expecting the creation to succeed.
    - Try to create a pod named `good-pod-2` whose image is `nginx` in the `staging-ns` namespace and the `allowPrivilegeEscalation` is set to `true`, expecting the creation to succeed.
    - Try to create a pod named `bad-pod-1` whose image is `busybox` in the `staging-ns` namespace and the `allowPrivilegeEscalation` is set to `true`, expecting the creation to fail.
    - Try to create a pod named `bad-pod-2` whose image is `nginx` in the `default` namespace and the `allowPrivilegeEscalation` is set to `true`, expecting the creation to fail.
