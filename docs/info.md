# Endpoint `/info`

O endpoint `/info` fornece detalhes sobre o ambiente em que o gateway está rodando.

---

## Método

### GET `/info`

Retorna informações sobre o ambiente do gateway.

## Retorno (exemplo)

```json
{
  "hostname": "gateway-container",
  "os.arch": "amd64",
  "java.version": "17.0.9",
  "java.vendor": "Eclipse Adoptium",
  ...
}
```
