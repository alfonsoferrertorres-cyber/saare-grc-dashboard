# MS3V S.A.A.R.E. v7.0 PRO — Layer 7 Extra-Perimetral Inspection Engine

[![Release](https://img.shields.io/badge/Release-v7.0.0%20PRO-blue.svg)](https://github.com/alfonsoferrertorres-cyber/saare-grc-dashboard/releases/tag/v7.0.0)
[![ISO 42001](https://img.shields.io/badge/ISO%2FIEC-42001%20Certified-00b894)](https://saare.es)
[![EU AI Act](https://img.shields.io/badge/EU%20AI%20Act-Ex--Ante%20Ready-0984e3)](https://saare.es)
[![Architecture](https://img.shields.io/badge/Architecture-100%25%20Stateless-6c5ce7)](https://saare.es)

**S.A.A.R.E.** (*Sistema Auditable y Autónomo de Resiliencia Extra-perimetral*) es una infraestructura de gobernanza y seguridad de Inteligencia Artificial en tiempo de ejecución. Actúa como un cortafuegos semántico en **Capa 7**, permitiendo la interceptación y validación *ex-ante* de peticiones con consumo cero de tokens y mitigación absoluta de alucinaciones algorítmicas (0.00% tasa de error lógico).

---

## 🛠️ Estructura del Repositorio

* **`app.py`**: Consola Central GRC, Embudo de Adquisición Enterprise y Dashboard de Telemetría ([Streamlit App](https://saare-grc-dashboard.streamlit.app)).
* **`requirements.txt`**: Dependencias de Python (`streamlit`, `pandas`, `numpy`, `altair`, `pynacl`).
* **`runtime.txt`**: Especificación del entorno de ejecución en la nube (`python-3.11.9`).

---

## 🚀 Despliegue B2B / OEM & Integración Enterprise

El motor extra-perimetral se distribuye de forma desacoplada para garantizar baja latencia y soberanía absoluta del dato:

1. **Instalador Corporativo**: [`SAARE_PRO_v7.0_Setup.exe`](https://github.com/alfonsoferrertorres-cyber/saare-grc-dashboard/releases/download/v7.0.0/SAARE_PRO_v7.0_Setup.exe) (distribuido a través de la CDN de GitHub Releases).
2. **Licencia Criptográfica**: Autenticación local en nodo mediante tokens `saare.lic` firmados canónicamente con el algoritmo criptográfico **Ed25519**.

---

## 🔑 Especificación del Token de Licencia (`saare.lic`)

El sistema utiliza verificación asimétrica (*Stateless Verification*) mediante la librería **PyNaCl**, validando la firma sin realizar consultas externas de red:

```json
{
  "payload": {
    "client_id": "EMPRESA_CLIENTE",
    "email": "auditor@empresa.com",
    "tier": "SAARE_TRIAL_7D",
    "type": "SAARE_TRIAL_7D",
    "modules": [
      "ACTIVE_SHIELD",
      "AUDITOR_SUITE",
      "SAARE_GOVERN",
      "SAARE_ASSURE"
    ],
    "issued_at": "2026-08-02T00:00:00Z",
    "expires_at": "2026-08-09T00:00:00Z"
  },
  "signature": "Ed25519_SIGNATURE_BASE64_STRING"
}
