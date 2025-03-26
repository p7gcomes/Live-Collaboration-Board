import { WebSocketServer } from 'ws';

const wss = new WebSocketServer({ port: 8080 });

wss.on('connection', (ws) => {
    console.log('Novo cliente conectado');
    
    ws.on('message', (message) => {
        console.log(`Mensagem recebida: ${message}`);
        
        // Reenvia a mensagem para todos os clientes conectados
        wss.clients.forEach(client => {
            if (client !== ws && client.readyState === 1) {
                client.send(message);
            }
        });
    });

    ws.on('close', () => {
        console.log('Cliente desconectado');
    });
});

console.log('Servidor WebSocket rodando na porta 8080');
