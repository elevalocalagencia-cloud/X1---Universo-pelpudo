# 🌐 WORKFLOW: /proxy-setup

## Quando usar
- Configurar novo proxy no perfil Octo
- Trocar proxy queimado
- Investigar fraud score alto de um IP

## Stack de proxy recomendada (ordem de preferência)

### Tier 1 — Para operação geral
**NodeMaven Sticky Residencial BR**
- Escolher: cidade BR da mesma UF do CEP de cobrança
- Sticky duration: 24h (manter mesmo IP durante a sessão)
- Protocolo: SOCKS5 ou HTTP (Octo suporta os dois)
- Fraud Score esperado: 20-40

### Tier 2 — Para gateways difíceis (Stripe, ClearSale)
**IPRoyal Mobile 4G BR** ou **Soax Mobile BR**
- ASN: Vivo (AS28573) / Claro (AS26615) / TIM (AS26615)
- Mobile 4G = carrrier-grade NAT = fraud score geralmente <20
- Custo: ~$60-90/mês
- Ideal pra: Stripe, Mercado Pago, PagSeguro

### Tier 3 — Emergência / teste gratuito
**Hotspot 4G do celular pessoal**
- Ativa hotspot, conecta PC
- Rodar IPQS → normalmente <20
- Não escala, mas útil pra confirmar se IP é o problema

### ❌ NÃO USAR
- IP residencial NEO/V.tal (AS8167) — fraud score 89, queimado
- Proxies gratuitos (Telegram, sites suspeitos) — fraud score >90 sempre
- Datacenter (AWS, Azure, GCP, OVH) — detectado instantaneamente

## Verificação de qualidade do proxy

Antes de usar qualquer proxy novo:
```
1. ipqualityscore.com → Fraud Score <40 / Proxy: False / VPN: False
2. whoer.net → 100% / Proxy: No / Blacklist: No
3. Se os dois passam → proxy aprovado
```

## Configuração no Octo Browser

Aba Geral → campo "Proxy" → formato:
```
socks5://usuario:senha@host:porta
ou
http://usuario:senha@host:porta
```

Após configurar:
- DNS no perfil: `1.1.1.1`
- Geolocalização: "Com base no IP"
- WebRTC: "Com base no IP"
- Salvar → fechar → reabrir perfil

## Sobre RTT alto (300-600ms)

É NORMAL em proxy residencial. Causa: backbone intercontinental do provider.
Soluções:
- Aceitar (impacto real em antifraude BR é baixo)
- Extensão de override (faz browser reportar effectiveType: 4g)
- Não tem como reduzir RTT real sem mudar tipo de proxy
