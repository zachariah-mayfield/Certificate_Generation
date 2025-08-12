# Certificate_Generation
Certificate_Generation

# Certificate Generation with Ansible

This project contains an Ansible role to generate a **Root Certificate Authority (CA)**,  
a **Vault server certificate**, and a **Vault client certificate** — all signed by the same CA.

It replicates the functionality of an OpenSSL bash script, but is implemented entirely in Ansible.

# The role will:
- Ensure the output directory exists
- Generate a Root CA key (4096-bit RSA)
- Generate a Root CA certificate
- Create an OpenSSL config file with SAN entries for vault_server
- Generate server key, CSR, and signed certificate
- Generate client key, CSR, and signed certificate
- Export the client certificate in PKCS#12 (.pfx) format
- All commands use the creates: argument so they run only if the file does not already exist.

---

## Generated Files

By default, all generated certificates and keys are placed in:

# 
You can change this path by overriding the `Out_Directory` variable.

The following files will be created:

| File | Description |
|------|-------------|
| `rootCA.key`  | Root CA private key |
| `rootCA.crt`  | Root CA certificate (self-signed) |
| `vault-server.key` | Server private key |
| `vault-server.csr` | Server Certificate Signing Request |
| `vault-server.crt` | Server certificate signed by Root CA |
| `vault-client.key` | Client private key |
| `vault-client.csr` | Client Certificate Signing Request |
| `vault-client.crt` | Client certificate signed by Root CA |
| `vault-client.pfx` | Client certificate and key in PKCS#12 format |

---

## Clone the repository
```bash
# bash
git clone https://github.com/<your-repo>/Certificate_Generation.git
cd Certificate_Generation/Ansible
```

# Create your Python Virtual Environment
```bash
# bash
sh "/GitHub/Main/Certificate_Generation/Scripts/Python_Virtual_Environment/setup_python_venv.sh"
source ~/GitHub/Main/Certificate_Generation/.venv/bin/activate
```

# Run the Ansible PlayBook:
```bash
# bash
ansible-playbook ~"/GitHub/Main/Certificate_Generation/Ansible/playbook_generate_root_ca_and_server_and_client_certs.yml"
```

