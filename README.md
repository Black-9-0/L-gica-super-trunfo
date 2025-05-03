# L-gica-super-trunfo

class SuperTrunfoGame {
  constructor() {
    this.deck = new Deck();
    this.players = [];
    this.currentRound = 0;
  }

  startGame(playerNames) {
    this.deck.createDeck();
    this.deck.shuffle();
    
    // Criar jogadores
    this.players = playerNames.map(name => new Player(name));
    
    // Distribuir cartas
    const cardsPerPlayer = Math.floor(this.deck.cards.length / this.players.length);
    this.players.forEach(player => {
      for (let i = 0; i < cardsPerPlayer; i++) {
        player.addCard(this.deck.cards.pop());
      }
    });
  }

  playRound() {
    this.currentRound++;
    
    const cardsInPlay = [];
    const attributesChosen = [];
    
    // Cada jogador joga uma carta
    for (const player of this.players) {
      const card = player.playCard();
      cardsInPlay.push({player, card});
      
      // Jogador escolhe atributo (simplificado)
      const attribute = player.chooseAttribute(card);
      attributesChosen.push(attribute);
    }
    
    // Determinar vencedor do round
    this.determineRoundWinner(cardsInPlay, attributesChosen);
  }

  determineRoundWinner(cardsInPlay, attributesChosen) {
    // Lógica simplificada para determinar vencedor
    // Implementação real precisa comparar os atributos escolhidos
    // e verificar cartas Super Trunfo
  }
}