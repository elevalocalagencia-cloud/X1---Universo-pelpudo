# 🔬 WORKFLOW: /antidetect-audit

## Quando usar
Sempre que Fernando criar um perfil novo no Octo ou trocar proxy.
Rodar a bateria completa antes de qualquer operação real.

## Pré-requisitos
- Octo Browser aberto com perfil configurado
- Proxy conectado e funcionando
- DNS 1.1.1.1 setado na aba Geral

## Bateria de testes (ordem obrigatória)

```
PASSO 1 → whoer.net
  → Esperado: 100% disguise / Proxy: No / Anonymizer: No / Blacklist: No
  → Se falhar: verificar proxy e DNS

PASSO 2 → pixelscan.net
  → Esperado: "consistent" + No proxy + No masking + No automated behavior
  → Se falhar: fingerprint com problema grave

PASSO 3 → iphey.com
  → Esperado: "Trustworthy" (verde)
  → Se "Suspicious": investigar qual campo falhou
  → Se "Untrustworthy": não operar, refazer perfil

PASSO 4 → browserscan.net
  → Esperado: >85% authenticity / DNS Leak: No / Proxy: Yes (aceitável)
  → Se <80%: verificar DNS leak e fingerprint

PASSO 5 → browserleaks.com/webrtc
  → Esperado: "No Leak" / Public IP = IP do proxy / Local IP = vazio
  → Se leaking: verificar WebRTC setting no Octo (tem que ser "Com base no IP")

PASSO 6 → browserleaks.com/webgl
  → Esperado: Unmasked Vendor = "Google Inc. (NVIDIA/Intel/AMD)"
  → Se Vendor = "WebKit" apenas (sem Debug Info real): setting de renderer incorreto

PASSO 7 → abrahamjuliot.github.io/creepjs
  → Esperado: Trust Score >70% / Lies = 0
  → Checar: Screen depth (tem que ser 24) / GPU / Timezone / Headless %

PASSO 8 → ipqualityscore.com (com o IP do proxy)
  → Esperado: Fraud Score <40 / VPN: False / Proxy: False / Bot: False
```

## Critério de aprovação para operar
- Todos os 8 passaram no esperado → ✅ PODE OPERAR
- 1-2 ⚠️ menores (headless 25%, effectiveType 3g) → ✅ PODE OPERAR (baixo impacto)
- Qualquer 🔴 crítico (leak, fraud score >75, Untrustworthy) → ❌ NÃO OPERAR

## Após aprovação: checklist pré-compra
- [ ] Proxy na mesma UF do CEP de cobrança
- [ ] Conta na loja criada 3-7 dias antes
- [ ] Email com 30+ dias de existência
- [ ] Navegar 5-10 min antes de abrir checkout
- [ ] Digitar cartão manualmente (NUNCA colar)
- [ ] Checkout durar mínimo 3 minutos
