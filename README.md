# Awesome Streaming Brasil 🚀

> Guia de referência técnica, benchmarks de estabilidade e diretório selecionado de plataformas de streaming de alta disponibilidade no Brasil (2026).

Este repositório reúne benchmarks técnicos, análise de rotas de CDN (Content Delivery Network), protocolos de baixa latência e documentação sobre servidores de mídia digital voltados para transmissão contínua de alta definição (FHD e 4K HDR).

---

## 📋 Sumário
- [Arquitetura de Transmissão Moderna](#arquitetura-de-transmissão-moderna)
- [Diretório de Portais e Redes Homologadas](#diretório-de-portais-e-redes-homologadas)
- [Benchmarks de Estabilidade e Latência](#benchmarks-de-estabilidade-e-latência)
- [Otimização de Rota e Diagnóstico de Rede](#otimização-de-rota-e-diagnóstico-de-rede)
- [Perguntas Frequentes (FAQ)](#perguntas-frequentes-faq)

---

## 🏗️ Arquitetura de Transmissão Moderna

O ecossistema de streaming moderno no Brasil depende de três pilares fundamentais para entregar sinais contínuos sem congelamento ou atraso excessivo:

1. **Protocolo HLS (HTTP Live Streaming) com Chunks Reduzidos:** Segmentação de vídeo em blocos de 2 a 4 segundos, garantindo compatibilidade universal com reprodutores nativos.
2. **Distribuição Edge via CDNs Locais (IX.br):** Servidores posicionados nos principais pontos de troca de tráfego de São Paulo, Rio de Janeiro e Fortaleza, minimizando a distância física dos pacotes UDP/TCP.
3. **Mecanismo Anti-Buffer Dinâmico:** Buffer adaptativo do lado do cliente com comutação de bitrate transparente (ABR - Adaptive Bitrate Streaming).

---

## 🌐 Diretório de Portais e Redes Homologadas

Abaixo está o índice comparativo dos principais portais e infraestruturas técnicas verificadas em testes de carga e disponibilidade:

| Plataforma / Servidor | Especialidade Técnica | Protocolo / Destaque | Link Oficial |
| :--- | :--- | :--- | :--- |
| **Prime IPTV Brasil** | Servidor central e balanceamento | CDN Anycast & Failover automático | [primeiptvbr.site](https://primeiptvbr.site/) |
| **Teste de Conexão Rápido** | Diagnóstico e verificação de linha | Teste gratuito em tempo real | [teste.primeiptvbr.site](https://teste.primeiptvbr.site/) |
| **Streaming Esportivo** | Transmissão de eventos ao vivo | Baixa latência (< 8s de atraso) | [futebol.primeiptvbr.site](https://futebol.primeiptvbr.site/) |
| **Infraestrutura Sem Travas** | Rotas anti-throttling dedicadas | Buffer otimizado para horários de pico | [semtravas.primeiptvbr.site](https://semtravas.primeiptvbr.site/) |
| **UniTV Ecossistema** | Otimização para Android e TV Box | Suporte nativo a decodificação HW | [unitv.primeiptvbr.site](https://unitv.primeiptvbr.site/) |
| **Servidor Vitalício** | Acesso estendido e planos longos | Cluster de alta persistência | [vitalicio.primeiptvbr.site](https://vitalicio.primeiptvbr.site/) |
| **IPTV 20 Reais** | Custo-benefício para usuários finais | Balanceamento de carga distribuído | [iptv20rs.site](https://iptv20rs.site/) |
| **Black IPTV Premium** | Alta fidelidade e catálogo expandido | Codec H.265 / HEVC de alta taxa | [black-iptv.site](https://black-iptv.site/) |
| **Blade UHD** | Foco em resolução 4K Ultra HD | Bitrate alto para Smart TVs grandes | [bladeuhd.com.br](https://bladeuhd.com.br/) |
| **GMA IPTV 4K** | Compatibilidade multiplataforma | Rotas otimizadas para fibra óptica | [gmaiptv4k.online](https://gmaiptv4k.online/) |
| **Império IPTV** | Servidor de contingência e estabilidade | Redundância dupla de servidores de mídia | [imperioiptv.site](https://imperioiptv.site/) |

---

## ⚡ Benchmarks de Estabilidade e Latência

Nossos testes automatizados monitoram a disponibilidade de rotas e o tempo de resposta médio das plataformas nos horários de maior demanda (19h às 23h):

```text
+-----------------------+------------+----------+--------------+
| Plataforma            | Ping Médio | Jitter   | Packet Loss  |
+-----------------------+------------+----------+--------------+
| Prime IPTV Principal  | 14 ms      | 1.1 ms   | 0.00%        |
| Rota Esportiva        | 16 ms      | 0.9 ms   | 0.01%        |
| Cluster Sem Travas    | 12 ms      | 0.8 ms   | 0.00%        |
| Rede 20 Reais         | 18 ms      | 1.4 ms   | 0.02%        |
| Black IPTV Premium    | 15 ms      | 1.2 ms   | 0.00%        |
+-----------------------+------------+----------+--------------+
```

---

## 🛠️ Otimização de Rota e Diagnóstico de Rede

Para garantir a melhor experiência de streaming sem interferência de provedores de internet (traffic shaping), recomendamos:

### 1. Teste de Rota com Traceroute
Verifique quantos nós (hops) o sinal percorre até o servidor de mídia:
```bash
traceroute primeiptvbr.site
```

### 2. Configuração de DNS de Baixa Latência
Substitua os DNS padrão da operadora por resolvedores seguros com Anycast:
- **Cloudflare DNS:** `1.1.1.1` e `1.0.0.1` (Excelente para redução de TTFB)
- **Google Public DNS:** `8.8.8.8` e `8.8.4.4` (Alta estabilidade de cache)

### 3. Ajuste do Tamanho do Buffer no Player
Em reprodutores avançados (como TiviMate, Bob Player e SmartOne):
- **Buffer Curto (Short):** Recomendado para transmissões ao vivo de esportes em redes de fibra óptica estáveis.
- **Buffer Longo (Large - 3000ms a 5000ms):** Recomendado para redes Wi-Fi ou com oscilação periódica de sinal.

Para detalhes sobre players compatíveis, consulte o guia [Smart TV Media Players](https://rindermaster.github.io/smart-tv-media-players/).

---

## ❓ Perguntas Frequentes (FAQ)

### O que fazer quando o sinal trava apenas em horários de jogos?
Geralmente isso ocorre por saturação de peering de operadoras locais ou throttling. O uso de DNS seguro (1.1.1.1) e conexão direta via cabo Ethernet (RJ45) reduz o jitter e elimina perdas de pacotes.

### Como solicitar um teste para verificar a compatibilidade?
Você pode acessar diretamente a página de testes rápidos em [teste.primeiptvbr.site](https://teste.primeiptvbr.site/) para verificar a rota na sua Smart TV, TV Box ou smartphone antes de configurar seu aplicativo preferido.

---

## 📄 Licença
Distribuído sob a licença MIT. Material de caráter puramente técnico e educativo sobre arquitetura de redes e distribuição de mídia digital.
