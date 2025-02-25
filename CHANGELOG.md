# Changelog

All notable changes of this project are documented in this file.

# v0.12.0

**Release date:** 2022-09-07

This release contains a number of new features and bug fixes.

New Features and Bug Fixing:
  * Enable custom backends for Terraform (@fsequeira1)
  * Support `backendConfigsFrom` for specifying backend configuration from Secrets (@chanwit)
  * Add a parameter for specifying max gRPC message size, default to 4MB (@chanwit)
  * Implement force-unlock for tfstate management (@Nalum)
  * Fix the initialization status (@chanwit)
  * Recording events to support Flux notification controller (@chanwit)
  * Support specifying targets for plan and apply (@akselleirv)
  * Add node selector, affinity and tolerations for the runner pod (@Nalum)
  * Add volume and volumeMounts for the runner pod (@steve-fraser)
  * Add file mapping to map files from Secrets to home or workspace directory (@itamar-marom)
  * Fix Plan prompt being overridden by the progressing message (@chanwit)
  * Support storing human-readable plan output in a ConfigMap (@chanwit)

# v0.11.0

**Release date:** 2022-08-12

This release is another milestone of the project as it is the first release of TF-controller
that supports Flux's OCIRepository.

New Features and Bug Fixing:
  * Added support for Flux's OCIRepository (@chanwit)
  * Fixed EnvVars to pick up `valueFrom` to work with Secrets and ConfigMaps (@Nalum)
  * Fixed tfctl to show plan in the working directory (@github-vincent-miszczak)
  * Updated tfexec to v0.16.1 for the force-lock option (@chanwit)
  * Updated the Source controller to v0.26.1 (@chanwit)

# v0.10.1

**Release date:** 2022-08-05

This release is a huge improvement as we have successfully reconciled 1,500 Terraform modules concurrently.
This pre-release contains the following changes.

Bug Fixing:
  * Fix pod deletion process (@chanwit)
  * Make the gRPC dial process more reliable (@chanwit)
  * Add the runner pod creation timeout, default at 5m0s (@chanwit)
  * Fix another race condition secret (@chanwit)
  * Map runner's home to a volume to make it writeable (@chanwit)

# v0.10.0

**Release date:** 2022-08-02

This pre-release contains the following changes.

New Features and Bug Fixing:
  * Add support for Terraform Enterprise (@chanwit)
  * Implement resource inventory (@chanwit)
  * Improve security to make the images work with Weave GitOps Enterprise (@chanwit)
  * Re-implement certificate rotator (@chanwit)
  * Correct IRSA docs (@benreynolds-drizly)
  * Update Kubernetes libraries to v0.24.3 (@chanwit)
  * Update go-restful to fix CVE-2022-1996 (@chanwit)
  * Add pprof to the /debug/pprof endpoint (@chanwit)
  * Fix race condition to make sure that gRPC client and the runner use the same TLS (@chanwit)

# v0.9.5

**Release date:** 2022-05-30

This pre-release contains the following changes.

New Features:
  * Update Terraform binary to 1.1.9 (@chanwit)
  * Allow runner pod metadata customization (@tomhuang12)
  * Support runner pod environment variables specification (@Nalum)
  * Implement `.spec.refreshBeforeApply` to refresh the state before apply (@chanwit)
  * Use controller runtime logging library in runner (@chanwit)

Bug Fixing:
  * Fix nil reference for event recorder (@chanwit)
  * Fix insertion of sensitive information to runner pod logging (@chanwit)
  * Fix nil reference for in writeBackendConfig (@chanwit)

# v0.9.4

**Release date:** 2022-04-15

This pre-release contains the following changes.

New Features and Bug Fixing:
  * Fix Helm chart to support image pull secrets for `tf-runner` Service Accounts (@Nalum)
  * Upgrade Source Controller API to v0.22.4 (@tomhuang12)
  * Fix json bytes encoding (@phoban01)
  * Add Helm chart an option to specify AWS Security Group policy (@Nalum)
  * Move plan revision from labels to annotations (@Nalum)
  * Update images to include fix for CVE-2022-28391 (@chanwit)
  * Update Terraform binary to 1.1.8 (@chanwit)

# v0.9.3

**Release date:** 2022-03-28

This pre-release contains the following changes.

Bug Fixing:
  * Fix runner pod pointer variables so that getting pods works correctly (@chanwit)

# v0.9.2

**Release date:** 2022-03-25

This pre-release contains the following changes.

Bug Fixing:
  * Wait for runner pods to be completely terminated before reconcile a new one (@chanwit)

# v0.9.0

**Release date:** 2022-03-21

This pre-release contains the following changes.

New Features and Bug Fixing:
  * Network-based health checks (@tomhuang12)
  * Improved drift detection status (@phoban01)
  * Add FOSSA and CodeQL scan (@tomhuang12)
  * Support HCL variables (@phoban01)
  * Implemented local gRPC runner (@chanwit)
  * Update source-controller to v0.21.1 (@tomhuang12)
  * Add Trivy scan (@tomhuang12)
  * Change image repository to ghcr.io/weaveworks (@phoban01)
  * Move repository to Weaveworks (@chanwit)
  * Add E2E Tests (@tomhuang12)
  * Moved charts to `weaveworks/tf-controller` (@tomhuang12)
  * Add local http server for http health check (@tomhuang12)
  * Update Terraform version (@fsequeira1)
  * Update the Helm repository URL (@tomhuang12)
  * Implement CA certification generation and mTLS rotation (@phoban01)
  * Add documentation site (@tomhuang12)
  * Implemented runner pods (@chanwit)
  * Add multi-tenancy E2E test case (@tomhuang12)
  * Implemented output name mapping (@chanwit)
  * Improve test coverage (@tomhuang12)
  * Fix documents GitHub Actions (@tomhuang12)
  * Set the default Service Account to `tf-runner` (@tomhuang12)
  * Make certification rotation configurable (@tomhuang12)
  * Implement gRPC retry policy (@chanwit)
  * Implement TLS validation and graceful shutdown (@phoban01)
  * Fix certification validation (@chanwit)
  * Fix drifted outputs (@chanwit)
  * Change the behaviour of pod cleanup to be default (@chanwit)
  * Add concurrency to the Helm chart (@chanwit)
  * Fix CVE-2022-0778 (@chanwit)

# v0.8.0

**Release date:** 2022-01-24

This pre-release contains the following changes.

Breaking Changes:
  * Change `.spec.varsFrom` from object to be an array of object in `v1alpha1`. Users require to update their Terraform objects.

New Features:
  * Helm chart (@tomhuang12)
  * Allow many instances of `.spec.varsFrom` (@phoban01)
  * Add the Drift Detection only mode (@phoban01)
  * Upgrade Terraform to 1.1.4 (@chanwit)

Improvements:
  * Fix recording the status of destroy plans (@chanwit)

# v0.7.0

**Release date:** 2022-01-16

This pre-release contains the following changes.

New Features:
  * Add flag to allow disabling drift detection `.spec.disableDriftDetection` (@phoban01)
  * Add field to allow specifying TF client configuration `.spec.cliConfigurationSecretRef` and disable backend completely `.spec.backendConfig.disable` (@chanwit)
  
Improvements:
  * Add documentation on how to use TF-controller with EKS IRSA (@phoban01)
  * Support gzip encoding for `tfplan` (@tomhuang12)
  * Improve re-plan behaviour (@chanwit)

## v0.6.0

**Release date:** 2022-01-12

This pre-release contains the following changes.

Improvements:
  * Correct the manual approval behaviour, as amended in [tc000030](controllers/tc000030_plan_only_no_outputs_test.go).
  * Upgrade Go to 1.17.6
  * Upgrade Source controller to v0.20.1
  * Support Flux v2 0.25.x

## v0.5.2

**Release date:** 2022-01-11

This pre-release contains the following changes.

Improvements:
  * Improve UX for plan generation message. Plan message now includes an action with the short form of the plan id, as amended in [tc000050](controllers/tc000050_plan_and_manual_approve_no_outputs_test.go).

## v0.5.1

**Release date:** 2022-01-10

This pre-release contains the following changes.

Improvements:
  * Improve UX for plan generation message. Plan name is shown in the message, so that it can be used for an approval, as amended in [tc000050](controllers/tc000050_plan_and_manual_approve_no_outputs_test.go).

## v0.5.0

**Release date:** 2022-01-09

This pre-release contains the following changes.

Improvements:
  * Improve status messages.
  * `shouldDetectDrift` is now specified by [tc000180](controllers/tc000180_should_detect_drift_test.go)

## v0.4.3

**Release date:** 2022-01-09

This pre-release contains the following changes.

Improvements:
  * Improve `shouldDetectDrift` logic for new objects

## v0.4.2

**Release date:** 2022-01-09

This pre-release contains the following changes.

Improvements:
  * Add resource's shortName
  * Add display columns to the CRD.

## v0.4.1

**Release date:** 2022-01-09

This pre-release contains the following changes.

Improvements:
  * Improve `shouldDetectDrift` logic. 
  * Improve the behaviour of the auto mode t0 be started over from planning when the `apply` process fail because of entity exists externally, as specified by [tc000170](controllers/tc000170_if_apply_error_we_should_delete_the_plan_and_start_over_test.go).

## v0.4.0

**Release date:** 2022-01-08

This pre-release contains the following changes.

Improvements:
  * Introduce `.status.lastPlannedRevision` to handle a case of source changes by non TF-files, as specified by [tc000160](controllers/tc000160_auto_applied_should_tx_to_plan_when_unrelated_source_changed_test.go)
  * Improve `shouldDetectDrift` logic using `.status.lastPlannedRevision`.
  
## v0.3.1

**Release date:** 2022-01-07

This pre-release ships with the following changes.

Improvements:
  * Upgrade the Terraform binary tp v1.1.3.
  * Improve the spec documentation of the test files. 

## v0.3.0

**Release date:** 2022-01-05

This pre-release ships with the implementation of the following features. 

New Features:
  * The ability to apply Terraform in the `auto` approval mode, as specified by [tc000010](controllers/tc000010_no_outputs_test.go).
  * Support backend configuration, as specified by [tc000020](controllers/tc000020_with_backend_no_outputs_test.go).
  * The ability to `plan` Terraform, as specified by [tc000030](controllers/tc000030_plan_only_no_outputs_test.go), and [tc000050](controllers/tc000050_plan_and_manual_approve_no_outputs_test.go).
  * Support outputs and selection of those outputs as secrets, as specified by [tc000040](controllers/tc000040_controlled_outputs_test.go) and [tc000041](controllers/tc000041_all_outputs_test.go).
  * Support variables, also from `Secrets` and `ConfigMaps`, as specified by [tc000060](controllers/tc000060_vars_and_controlled_outputs_test.go), [tc000070](controllers/tc000070_varsfrom_secret_and_controlled_outputs_test.go), [tc000080](controllers/tc000080_varsfrom_configmap_and_controlled_outputs_test.go), [tc000090](controllers/tc000090_varsfrom_override_and_controlled_outputs_test.go).
  * The ability to reconcile when Source changes, as specified by [tc000100](controllers/tc000100_applied_should_tx_to_plan_when_source_changed_test.go), and [tc000110](controllers/tc000110_auto_applied_should_tx_to_plan_then_apply_when_source_changed_test.go).
  * Resource deletion implementation, as specified by [tc000120](controllers/tc000120_delete_test.go).
  * Support the `destroy` mode, as specified by [tc000130](controllers/tc000130_destroy_no_outputs_test.go).
  * Support drift detection, as specified by [tc000140](controllers/tc000140_auto_applied_should_tx_to_plan_then_apply_when_drift_detected_test.go) and [tc000150](controllers/tc000150_manual_apply_should_report_and_loop_when_drift_detected_test.go).
