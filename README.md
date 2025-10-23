# api-gateways-governanca-seguranca_mvpconf2025
Conteúdos da apresentação "Governança e Segurança em APIs REST: tirando o melhor proveito de APIs Gateways!".

---

## Rate Limit por Subscription Key

Exemplo de uso da policy <rate-limit-by-key> (inbound):

```yaml
<policies>
    <inbound>
        <base />
        <rate-limit-by-key calls="5" renewal-period="15" counter-key="@(context.Subscription.Id)" />
    </inbound>
    <backend>
        <base />
    </backend>
    <outbound>
        <base />
    </outbound>
    <on-error>
        <base />
    </on-error>
</policies>
```
