# 🕵️ SKILL: antidetect-specialist

## Quando ativar
- Usuário fala em proxy, antidetect, fingerprint, gateway, aprovação
- Testes CreepJS / Pixelscan / IPhey / BrowserScan / Whoer
- Configuração do Octo Browser
- Stack de proxy (NodeMaven, IPRoyal, Soax, GeeLark, Multilogin)

## Protocolo de ativação

1. Ler SEMPRE o scratchpad antes de responder: `.agents/scratchpad.md`
2. Verificar qual teste está pendente
3. Quando receber print → analisar field por field
4. Nunca repetir diagnóstico já feito (economizar tokens)
5. Foco em ação concreta, não teoria

## Stack do usuário
- Octo Browser 2.10.9 (Windows)
- NodeMaven sticky residencial (Unifique SC AS28343)
- Casa: NEO/V.tal AS8167 — QUEIMADA, não usar
- Gateways: Stripe, MercadoPago, PagSeguro, ClearSale, VTEX, NuvemShop, Amazon BR

## Ordem de prioridade ao diagnosticar
1. Fraud Score do IP (IPQS) — se >75, troca proxy
2. WebRTC leak — se leaking IP real, corrigir primeiro
3. Pixelscan consistent — se failing, parar tudo
4. CreepJS Lies — cada lie é flag crítico
5. Screen depth — tem que ser 24 (não 30)
6. WebGL vendor — tem que ser NVIDIA/Intel real (não WebKit genérico)
7. effectiveType — 3g é ruim mas aceitável; 4g via extensão é opcional

## Frases de diagnóstico rápido
- "Fraud Score X" → <30 ✅ / 30-75 ⚠️ / >75 🔴
- "depth: 30" → 🔴 bug Octo, recriar perfil
- "depth: 24" → ✅
- "Proxy: True" no IPQS → ⚠️ proxy está sendo detectado
- "Proxy: False" no IPQS → ✅ limpo
- "Trustworthy" no IPhey → ✅ operar
- "Suspicious" no IPhey → ⚠️ investigar qual signal falhou
