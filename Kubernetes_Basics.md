Here are **clear, structured notes** on **Kubernetes Objects** based on your content:

---

# 📘 Kubernetes Objects – Notes

## 1️⃣ What Are Kubernetes Objects?

* **Kubernetes objects** are **persistent entities** in a Kubernetes cluster.
* They represent the **state of your cluster**.
* They act as a **record of intent** — once created, Kubernetes continuously works to maintain them.

They describe:

* What containerized applications are running (and on which nodes)
* Resources available to applications
* Application behavior policies (restart policy, scaling, updates, fault tolerance)

---

## 2️⃣ Desired State vs Actual State

Kubernetes follows a **declarative model**:

* When you create an object, you define the **desired state**.
* The Kubernetes control plane continuously works to make the **actual state match the desired state**.

If there is a difference (for example, a Pod crashes), Kubernetes automatically corrects it.

---

## 3️⃣ Object Structure: Spec and Status

Most Kubernetes objects contain two important nested fields:

### 🔹 `spec`

* Defines the **desired state**
* Set by the user when creating the object
* Example:

  * Number of replicas
  * Container image
  * Ports
  * Resource limits

### 🔹 `status`

* Represents the **current/actual state**
* Automatically updated by Kubernetes
* Managed by the control plane

### Example (Deployment):

If `spec.replicas = 3`:

* Kubernetes ensures 3 Pods are running
* If 1 fails, Kubernetes creates a new one
* `status` reflects the real-time state

---

## 4️⃣ Working with Kubernetes Objects

You interact with objects using:

* **Kubernetes API**
* **kubectl CLI**
* Client libraries (Go, Python, etc.)

Example command:

```
kubectl apply -f deployment.yaml
```

`kubectl` converts YAML → JSON and sends it to the API server.

---

## 5️⃣ Kubernetes Manifest Files

Objects are usually defined in **YAML files** (can also use JSON).

These files are called **manifests**.

---

## 6️⃣ Required Fields in a Kubernetes Object

Every Kubernetes manifest must include:

### 🔹 `apiVersion`

* Version of Kubernetes API used
* Example: `apps/v1`

### 🔹 `kind`

* Type of object
* Example: `Deployment`, `Pod`, `Service`

### 🔹 `metadata`

* Identifies the object
* Includes:

  * `name`
  * `namespace` (optional)
  * `UID`

### 🔹 `spec`

* Desired configuration of the object

---

## 7️⃣ Example: Deployment YAML

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```

### What this does:

* Creates a Deployment named `nginx-deployment`
* Runs 2 replicas
* Uses nginx image version 1.14.2
* Exposes container port 80

---

## 8️⃣ Different Objects Have Different Specs

The `.spec` field differs depending on object type.

Examples:

* **Pod** → Defines containers, volumes, restart policy
* **Deployment** → Defines replicas and Pod template
* **StatefulSet** → Defines stateful applications and Pod template

Each object type has its own API specification.

---

## 9️⃣ Server-Side Field Validation (Kubernetes v1.25+)

Starting from **Kubernetes v1.25**, the API server performs field validation.

This detects:

* Unknown fields
* Duplicate fields
* Invalid configurations

### Validation Modes (kubectl --validate)

| Mode                  | Description                      |
| --------------------- | -------------------------------- |
| `strict` (or `true`)  | Fails on validation errors       |
| `warn`                | Shows warnings but does not fail |
| `ignore` (or `false`) | Skips validation                 |

Default:

```
kubectl --validate=true
```

(which equals strict)

If API server does not support server-side validation:

* kubectl falls back to client-side validation.

Kubernetes v1.27+ always supports server-side validation.

---

# 🔟 Key Takeaways

* Kubernetes objects represent cluster state.
* They follow a **declarative model**.
* `spec` = desired state.
* `status` = current state.
* Kubernetes continuously reconciles spec and status.
* YAML manifests define objects.
* Required fields: `apiVersion`, `kind`, `metadata`, `spec`.
* Validation helps prevent configuration errors.

---

If you'd like, I can also give:

* 📝 Short exam-ready notes
* 📊 Diagram explanation
* 🎯 Interview questions
* 🧠 Mind map summary
* 🧪 Practical examples

Just tell me what format you prefer.

