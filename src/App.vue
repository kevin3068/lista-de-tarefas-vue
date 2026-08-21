<template>
  <div class="container">
    <h1>🎬 Gerador de Citações Aleatórias</h1>
    
    <div class="quote-box">
      <p class="quote-text">{{ quotaAtual.texto }}</p>
      <p class="quote-author">— {{ quotaAtual.autor }}</p>
    </div>

    <button @click="gerarNovaQuota" class="btn">
      Próxima Citação
    </button>

    <div class="stats">
      <p>Citações vistas: {{ contagem }}</p>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const quotas = [
  { texto: "A vida é 10% do que acontece com você e 90% de como você reage.", autor: "Charles R. Swindoll" },
  { texto: "O único jeito de fazer um grande trabalho é amar o que você faz.", autor: "Steve Jobs" },
  { texto: "Inovação distingue um líder de um seguidor.", autor: "Steve Jobs" },
  { texto: "A criatividade é a inteligência se divertindo.", autor: "Albert Einstein" },
  { texto: "Você não pode crescer sem sair da sua zona de conforto.", autor: "Stephen Covey" },
  { texto: "Sucesso é a soma de pequenos esforços repetidos dia após dia.", autor: "Robert Collier" },
  { texto: "Não há atalhos para qualquer lugar que valha a pena ir.", autor: "Beverly Sills" },
  { texto: "Acredite em si mesmo. Você é mais capaz do que pensa.", autor: "Benjamin Franklin" }
]

const contagem = ref(0)
const quotaAtual = ref(quotas[0])

const gerarNovaQuota = () => {
  const indice = Math.floor(Math.random() * quotas.length)
  quotaAtual.value = quotas[indice]
  contagem.value++
}
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.container {
  background: white;
  padding: 50px;
  border-radius: 20px;
  box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
  max-width: 600px;
  text-align: center;
}

h1 {
  color: #333;
  margin-bottom: 40px;
  font-size: 28px;
}

.quote-box {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 40px;
  border-radius: 15px;
  margin-bottom: 30px;
  min-height: 200px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.quote-text {
  font-size: 20px;
  font-weight: 500;
  margin-bottom: 20px;
  line-height: 1.6;
}

.quote-author {
  font-size: 16px;
  opacity: 0.9;
  font-style: italic;
}

.btn {
  background: #667eea;
  color: white;
  border: none;
  padding: 15px 40px;
  font-size: 16px;
  border-radius: 10px;
  cursor: pointer;
  font-weight: bold;
  transition: 0.3s;
}

.btn:hover {
  background: #764ba2;
  transform: translateY(-2px);
  box-shadow: 0 10px 20px rgba(102, 126, 234, 0.4);
}

.stats {
  margin-top: 30px;
  color: #666;
  font-size: 14px;
}
</style>
