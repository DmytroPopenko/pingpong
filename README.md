# pingpong
d;lksakl;dsak;l

<br>


<details>
<summary>;lkdsakl;dsa</summary>
fdlskfjlkdsk;fds
</details>


<code>
from pygame import *
init()\

img_back = "background.jpg"
img_ball = "ball.png"
img_hero = "platform.png"

win_width = 700
win_height = 500
display.set_caption("PingPong")
window = display.set_mode((win_width, win_height))
background = transform.scale(image.load(img_back), (win_width, win_height))
player_left = transform.rotate(image.load(img_hero), 180)

class GameSprite(sprite.Sprite):
    # конструктор класу
    def __init__(self, player_image, player_x, player_y, size_x, size_y, player_speed):
        # викликаємо конструктор класу (Sprite):
        sprite.Sprite.__init__(self)
        # кожен спрайт повинен зберігати властивість image - зображення
        self.image = transform.scale(
            image.load(player_image), (size_x, size_y))
        self.speed = player_speed


        # кожен спрайт повинен зберігати властивість rect - прямокутник, в який він вписаний
        self.rect = self.image.get_rect()
        self.rect.x = player_x
        self.rect.y = player_y


    # метод, що малює героя на вікні
    def reset(self):
        window.blit(self.image, (self.rect.x, self.rect.y))


class PlayerLeft(GameSprite):
    def update(self):
        keys = key.get_pressed()
        if keys[K_w] and self.rect.y > 5:
            self.rect.y -= self.speed
        if keys[K_s] and self.rect.y < win_height:
            self.rect.y += self.speed

ping_left = PlayerLeft(img_hero, 5, win_height - 100, 20, 150, 10)

run = True

while run:
    # подія натискання на кнопку Закрити
    for e in event.get():
        if e.type == QUIT:
            run = False
    window.blit(background, (0, 0))
    ping_left.update()
    ping_left.reset()

    display.update()
    time.delay(50)
</code>
