-- script.lua
-- Script básico de personagem usando LOVE2D

-- Definição do personagem
player = {
    name = "Gabriel",
    x = 100,
    y = 100,
    speed = 200
}

-- Carrega recursos
function love.load()
    love.graphics.setFont(love.graphics.newFont(14))
end

-- Atualiza a lógica do jogo
function love.update(dt)
    if love.keyboard.isDown("right") then
        player.x = player.x + player.speed * dt
    elseif love.keyboard.isDown("left") then
        player.x = player.x - player.speed * dt
    end

    if love.keyboard.isDown("down") then
        player.y = player.y + player.speed * dt
    elseif love.keyboard.isDown("up") then
        player.y = player.y - player.speed * dt
    end
end

-- Desenha na tela
function love.draw()
    love.graphics.print("Personagem: " .. player.name, 10, 10)
    love.graphics.rectangle("fill", player.x, player.y, 30, 30)
    love.graphics.print("Use as setas do teclado para mover Gabriel", 10, 30)
end
