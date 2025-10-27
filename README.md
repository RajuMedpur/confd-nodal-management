# confd-nodal-management
Emulate Netconf and CLI using Confd 


confd-nodal-mgmt/
├── .github/
│   └── workflows/
│       └── ci.yaml                  # GitHub Actions for CI/CD
├── confd/
│   ├── confd.conf                   # ConfD config with RESTCONF enabled
│   ├── confd-cdb/                   # Initial CDB data
│   ├── confd-cli/                   # CLI templates
│   ├── confd-netconf/               # NETCONF templates
│   ├── confd-restconf/              # RESTCONF templates (optional)
│   └── yang/                        # YANG modules
│       ├── interfaces.yang
│       └── system.yang
├── consumer-app/
│   ├── app.py                       # Python RESTCONF client
│   ├── requirements.txt
│   └── Dockerfile                   # Container for consumer app
├── docker/
│   ├── Dockerfile.confd             # ConfD container build
│   └── Dockerfile.base              # Optional base image for reuse
├── k8s/
│   ├── namespace.yaml               # Defines 'nodal-mgmt' namespace
│   ├── configmap.yaml               # Inject YANG/configs into ConfD
│   ├── confd-deployment.yaml        # ConfD pod in 'nodal-mgmt'
│   ├── confd-service.yaml           # ClusterIP or NodePort for ConfD
│   ├── consumer-deployment.yaml     # Consumer app pod in same namespace
│   ├── consumer-service.yaml        # Optional internal service
│   └── network-policy.yaml          # Optional: restrict access to ConfD
├── scripts/
│   ├── build.sh                     # Build Docker images
│   ├── deploy.sh                    # Deploy to Minikube
│   └── validate.sh                  # Validate NETCONF/RESTCONF behavior
├── tests/
│   ├── test_netconf.py              # ncclient tests
│   ├── test_restconf.py             # RESTCONF API tests
│   └── test_cli.exp                 # CLI expect script
├── docs/
│   ├── architecture.md              # System overview and diagrams
│   ├── onboarding.md               # Setup guide for new collaborators
│   └── yang-guide.md                # How to extend YANG modules
├── .gitignore
├── README.md
└── LICENSE
