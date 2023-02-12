--------------------------------------------------------------------------------
= Kubernetes the Hard Way =
--------------------------------------------------------------------------------
Components that are required in the project
  * kubernetes
  * containerd
  * coredns
  * cni
  * flannel
  * etcd
  * ngix


  kubernetes:
    Kubernetes, also known as K8s, is an open source system for managing
    containerized applications across multiple hosts. It provides basic
    mechanisms for deployment, maintenance, and scaling of applications.

  containerd:
    containerd is an industry-standard container runtime with an emphasis on
    simplicity, robustness, and portability. It is available as a daemon for
    Linux and Windows, which can manage the complete container lifecycle of its
    host system: image transfer and storage, container execution and
    supervision, low-level storage and network attachments, etc.

  coredns:
    CoreDNS is a DNS server/forwarder, written in Go, that chains plugins. Each
    plugin performs a (DNS) function.

  cni:
    CNI (Container Network Interface), a Cloud Native Computing Foundation
    project, consists of a specification and libraries for writing plugins to
    configure network interfaces in Linux containers, along with a number of
    supported plugins. CNI concerns itself only with network connectivity of
    containers and removing allocated resources when the container is deleted.
    Because of this focus, CNI has a wide range of support and the specification
    is simple to implement.

  Flannel:
    Flannel is a simple and easy way to configure a layer 3 network fabric
    designed for Kubernetes.

  etcd:
    etcd is a distributed reliable key-value store for the most critical data of a
    distributed system, with a focus on being:
      * Simple: well-defined, user-facing API (gRPC)
      * Secure: automatic TLS with optional client cert authentication
      * Fast: benchmarked 10,000 writes/sec
      * Reliable: properly distributed using Raft

  NGINX:
    http load balancer
--------------------------------------------------------------------------------

== Kubernets Project architecture
==
                  - Controller 1 ------------------------------+------------ Controller 2
                    * etcd                                     |             * etcd
                    * kube-apiserver                           |             * kube-apiserver
                    * NGINX - :80/healthz > :6443/healthz      |             * NGINX - :80/healthz > :6443/healthz
                    * Kube-controller-manager                  |             * Kube-controller-manager
                    * Kube-scheduler                           |             * Kube-scheduler
                                                               |
Remote KUBECTL---------------------------------------Kube API Load Balancer
                                                            * NGINX
                                                               |
                  - Worker 1 ----------------------------------+----------- Worker 1
                    * containerd                                            * containerd
                    * kubelet                                               * kubelet
                    * kube-proxy                                            * kube-proxy

--------------------------------------------------------------------------------
== Client Tools ==
  cfss                       | Tools used to manage certificates
                             |
  kubectl                    | The Kubernetes client used to interact with the
                             | cluster
                             |
--------------------------------------------------------------------------------
== Why Do We Need a CA and TLS Certificates? ==
  The Certificate Authority  | A certificate authority (CA) is used to generate
  and Certificates           | certificates
                             |
  Certificates               | Certificates are used to confirm (authenticate)
                             | identity. They are used to prove that you are who
                             | you say you are
                             |
  Certificate Authority (CA) | A Certificate Authority provieds the ability to
                             | confirm that a certificate is valid. A certificate
                             | authority can be used to validate any certificate
                             | that was issued using that certificate authority
                             |
                             | Kubernetes uses certificates for a variety of
                             | security functions, and the different parts of
                             | our cluste rwill validate certificates using the
                             | certificate authority.
                             |
  What Certificates do we    | After the certificate authority is provisioned,
  need?                      | the following certificates will need to be
                             | generated
                             |
                             | * *Client Certificates* - These certificates provide
                             |   client authentication for varous users: admin,
                             |   kube-controller-manager, kube-proxy, kube-scheduler,
                             |   and the kubelet client on each worker node
                             |
                             | * *Kubernetes API Server Certificate* - This is the
                             |   TLS certificate for the Kubernetes API
                             |
                             | * *Service Account Key Pair* - Kubernetes uses a
                             |   certificate to sign service account tokens, so
                             |   we need to provide a certificate for that purpose
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
