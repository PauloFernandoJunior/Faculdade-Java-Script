// Função para verificar se um número é primo
function isPrime(num) {
    if (num <= 1) return false; // Números menores ou iguais a 1 não são primos
    if (num <= 3) return true; // 2 e 3 são primos

    // Eliminar múltiplos de 2 e 3
    if (num % 2 === 0 || num % 3 === 0) return false;

    // Verificar se num é divisível por qualquer número até a raiz quadrada de num
    for (let i = 5; i * i <= num; i += 6) {
        if (num % i === 0 || num % (i + 2) === 0) return false;
    }

    return true;
}

// Função para encontrar os 10 maiores números primos a partir de um número fornecido pelo usuário
function findLargestPrimes() {
    const userNumber = parseInt(prompt("Digite um número: "), 10);

    if (isNaN(userNumber)) {
        console.log("Por favor, insira um número válido.");
        return;
    }

    const primes = [];
    let currentNumber = userNumber;

    while (primes.length < 10) {
        if (isPrime(currentNumber)) {
            primes.push(currentNumber);
        }
        currentNumber++;
    }

    console.log("Os 10 maiores números primos a partir de", userNumber, "são:", primes);
}

// Executar a função para encontrar os 10 maiores números primos
findLargestPrimes();
