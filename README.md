# 📘 Documentação – Pomodoro Timer (Vue + TS + SCSS)

## 📌 Descrição do Projeto

Um aplicativo Pomodoro feito com **Vue 3, TypeScript e SCSS**.
O usuário alterna entre períodos de foco e descanso.
Quando o tempo acaba, aparece um modal vermelho com animação de zoom + um som de alarme.
Durante o tempo de foco, uma música de concentração toca em loop até o ciclo terminar.

Ideal para estudar, trabalhar e manter o foco sem desculpas. 😎

## 🚀 Funcionalidades

| Funcionalidade | Status |
|----------------|--------|
| Cronômetro com contagem regressiva | ✅ |
| Alternância automática foco ↔️ descanso | ✅ |
| Modal de aviso quando tempo termina | ✅ |
| Animação de zoom no modal | ✅ |
| Som de alarme ao finalizar ciclo | ✅ |
| Música de foco durante o período de foco | ✅ |
| Pausar/Resetar timer mantendo lógica de áudio | ✅ |

## 🏗️ Tecnologias Utilizadas

- Vue 3
- TypeScript
- SCSS
- Composition API
- HTML Audio API

## 📁 Estrutura de Pastas

```css
src/
 ├── components/
 │   ├── PomodoroTimer.vue
 │   └── TimerModal.vue
 ├── App.vue
 ├── main.ts
 └── globals.scss
public/
 ├── alarm.mp3
 └── lofi-focus.mp3
```

## ⚙️ Instalação e Execução

- Clonar o repositório

```bash
git clone https://github.com/seu-usuario/pomodoro-vue-ts.git
cd pomodoro-vue-ts
```

- Instalar dependências

```bash
npm install
```

- Executar em modo desenvolvimento

```bash
npm run dev
```

## 🎮 Como usar

- Clique em Start para iniciar o ciclo
- Pause pausa a contagem e a música
- Reset inicia novamente o tempo atual
- Ao terminar o tempo → modal aparece + alarme toca
- Após fechar modal → muda automaticamente para o próximo modo (foco → descanso ou descanso → foco)

## ⏱️ Lógica do Pomodoro

| Modo | Tempo padrão |
|------|--------------|
| Foco | 25:00 |
| Descanso curto | 05:00 |

> Quando o modo foco termina, toca o alarme e para a música.<br/>
> Quando inicia novo ciclo de foco → música começa novamente.

## 🔊 Gerenciamento de Áudio

| Situação | Música foco | Alarme |
|----------|-------------|--------|
| Inicia foco | ▶️ | ❌ |
| Pausa timer | ⏸️ | ❌ |
| Reseta timer | ⏹️ | ❌ |
| Ciclo foco termina | ⏹️ | ▶️ |
| Modo descanso | ❌ | ❌ |

## 🎨 Animação do Modal

- Animação de zoom pulsante
- Fundo vermelho com opacidade
- Conteúdo centralizado e chamativo

**Keyframe utilizado:**

```css
@keyframes zoomPulse {
  0% { transform: scale(1); }
  50% { transform: scale(1.15); }
  100% { transform: scale(1); }
}
```

## 🧠 Regras do Timer

- Não cria múltiplos intervalos ao clicar Start várias vezes
- Timer sempre é limpo antes de reiniciar
- Timer reseta automaticamente após fim do ciclo
- Alternança automática entre modos

## 🔒 Boas práticas aplicadas

- ✅ Uso de ref<number | null> para evitar any
- ✅ Limpeza do intervalo com onUnmounted
- ✅ Separação de componentes (SOLID feelings 😌)
- ✅ SCSS scoped para evitar treta global
- ✅ Áudio controlado pelo estado do timer

## 🔧 Possíveis Próximas Melhorias

- Configurar tempos via UI
- Volume e botão mute para música e alarme
- Gráfico/contador de ciclos concluídos
- Animações de transição do timer
- Notificações desktop quando tempo termina
- Opções de música via lista
- Timer longo após X ciclos

## 👨‍💻 Desenvolvedor

Projeto desenvolvido por [Felipe Mascena](https://www.linkedin.com/in/felipe-mascena/) para estudo de **Vue 3** com **TypeScript**
e para ajudar você a manter o foco sem surtar 😅

## 📄 Licença

> MIT — pode usar, modificar e distribuir à vontade 🎉