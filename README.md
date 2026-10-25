<h1 align="center">Hi, I'm Omar</h1>
<h3 align="center">DevSecOps &amp; Platform Engineer &nbsp;·&nbsp; Offensive Security (Web &amp; Active Directory)</h3>

<p align="center">
  I build secure, reproducible platforms — and, as a separate craft, I break into web applications and
  Active Directory to understand how they fail. <b>Two distinct fields</b>, kept deliberately apart, each pursued in depth.
</p>

---

## DevOps / DevSecOps & Platform Engineering

I build platforms where every deploy is a git commit and the cluster heals itself back to what's declared. A few decisions from running a 15+ service system on **k8s**:

- **CI bumps the image tag in a separate manifests repo; ArgoCD reconciles from there.** Splitting the app repos from the GitOps source-of-truth keeps deploys auditable and revertable, and stops a bad build from touching the cluster directly.
- **Database-per-service, never a shared DB.** Services talk synchronously over REST and asynchronously via RabbitMQ events, so one service's schema can't quietly couple to another's.
- **Hit the Gateway API's 16-rule HTTPRoute cap at 15 services** — split routing across a second HTTPRoute that merges on the same gateway/host, rather than collapsing path prefixes and losing clarity.
- **Security lives in the pipeline, not a checklist after the fact** — Sealed Secrets committed encrypted, image/dependency scanning (Trivy), static analysis (Semgrep), runtime detection (Falco).
- **Portable IaC (Terraform + Ansible)** — the same stack rebuilds on any provider or bare metal, with no lock-in.

---

## Offensive Security · Web Applications & Active Directory

I learn this by building the target, then breaking it — standing up full Active Directory environments from scratch, and doing web application pentesting hands-on during my internship at Maroc Telecom — so I understand *why* an attack works, not just which tool to run.

- **Built an end-to-end AD CS ESC1 lab** — one `vagrant up` provisions a Domain Controller, Enterprise CA, Windows 10 and Kali on libvirt/KVM, then walks the chain: enumerate the vulnerable template → request a cert as a privileged user → PKINIT → DCSync.
- **Building the domain forces the fundamentals** — Kerberos, certificate templates, ACLs and delegation — that running a tool against someone else's box never teaches.
- **Both sides of each path** — enumeration, privilege escalation and lateral movement, plus the hardening that shuts each one down.
- **Built MT-Scan, an internal recon and vulnerability-scanning platform**, during my pentesting internship at Maroc Telecom — 15 tools (masscan, nmap, nuclei, ffuf, gobuster, subfinder, testssl.sh, and more) behind one plugin interface, with active scans gated by a code-enforced target allowlist instead of operator discipline.

---

### Featured work

**Platform / DevSecOps**

**Lotus Capital · DevSecOps internship** — the infrastructure for two of the company's platforms, both rebuilt from Git.
- **[`trading-platform-infra`](https://github.com/omar1111eamsa/trading-platform-infra)** — six-service trading platform on **k3s**: blocking security gates in CI, the image tag is the git SHA committed back to Git, **ArgoCD** with prune + selfHeal, rollback = `git revert`.
- **[`portable-platform-infra`](https://github.com/omar1111eamsa/portable-platform-infra)** — ~25 services including an **Airflow** pipeline on a 3-node k3s cluster: one `terraform apply` creates the VMs, runs **Ansible** and hands over to ArgoCD, on any cloud or bare metal.

**AWS EKS**
- **[`online-boutique-platform`](https://github.com/omar1111eamsa/online-boutique-platform)** — 11 microservices on **EKS** with **Karpenter**, ArgoCD, GitHub OIDC (no static AWS keys), and a DR runbook of every real failure and its fix.
- **[`cymbal-bank-infrastructure`](https://github.com/omar1111eamsa/cymbal-bank-infrastructure)** — zero-trust banking platform on EKS: **Cilium** (eBPF) default-deny policies, **Istio** Ambient Mesh, AWS WAF, HCP Terraform.

**Airbnb-clone microservices platform** — a production-style system, fully GitOps-managed.
- **[`my-airbnb/k8s-manifests`](https://github.com/my-airbnb/k8s-manifests)** — GitOps source-of-truth: 15+ Spring Boot services and a Next.js frontend on **k3s**, deployed by **ArgoCD** with **NGINX Gateway Fabric**, Sealed Secrets, and HPA autoscaling.
- **[`my-airbnb/infra`](https://github.com/my-airbnb/infra)** — the IaC that stands it up: **Terraform** (AWS) + **Ansible** (k3s, ArgoCD, cert-manager, Sealed Secrets, Falco).

**Offensive Security**

**[`ad-attack-scenario`](https://github.com/omar1111eamsa/ad-attack-scenario)** — a build-it-then-break-it **Active Directory** lab: one `vagrant up` provisions a Domain Controller, Enterprise CA, Windows 10 and Kali (libvirt/KVM), then walks an **AD CS ESC1** attack end-to-end (enumerate → cert-as-admin → PKINIT → DCSync). Learn how a pentest really works by building the target and breaking it.

**[`mt-scan`](https://github.com/omar1111eamsa/mt-scan)** — an on-demand recon and vulnerability-scanning platform (**Go** API/worker, Postgres-backed task queue, **Next.js** UI), built during my pentesting internship at **Maroc Telecom**. 15 tools behind one plugin interface, findings persisted and diffable across re-scans instead of scattered across local files, active scans gated by a code-enforced allowlist — not operator discipline.

---

### Core stack

**Platform / DevSecOps**
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)
![ArgoCD](https://img.shields.io/badge/Argo_CD-EF7B4D?style=for-the-badge&logo=argo&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=for-the-badge&logo=terraform&logoColor=white)
![Ansible](https://img.shields.io/badge/Ansible-EE0000?style=for-the-badge&logo=ansible&logoColor=white)
![Trivy](https://img.shields.io/badge/Trivy-1904DA?style=for-the-badge&logo=aquasecurity&logoColor=white)
![Falco](https://img.shields.io/badge/Falco-00AEC7?style=for-the-badge&logo=falco&logoColor=white)
![Sealed Secrets](https://img.shields.io/badge/Sealed_Secrets-555?style=for-the-badge&logo=kubernetes&logoColor=white)

**Offensive Security**
![Active Directory](https://img.shields.io/badge/Active_Directory-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![Kali Linux](https://img.shields.io/badge/Kali_Linux-557C94?style=for-the-badge&logo=kalilinux&logoColor=white)
![BloodHound](https://img.shields.io/badge/BloodHound-C00000?style=for-the-badge&logoColor=white)

<sub>Also working with: Docker · Helm · GitHub Actions · Semgrep · AWS · Cloudflare · NGINX · Go · Java/Spring Boot · Next.js/TypeScript · Python · PostgreSQL · MongoDB · Neo4j · Redis · RabbitMQ</sub>

---

### Reach me

[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:oserghini090@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/omar-serghini-a44187339/)

<p align="center"><i>Secure by default · Automated by design · Reproducible by commit.</i></p>
