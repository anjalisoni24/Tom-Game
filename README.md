import pygame
import random
import time
from pygame.locals import*
pygame.init()
b=900
a=700
screen=pygame.display.set_mode((b,a))
class Tom(pygame.sprite.Sprite):
    def __init__(self):
        super(). __init__()
        self.image=pygame.image.load("tom.png").convert_alpha()
        self.image=pygame.transform.scale(self.image,(100,500))
        self.rect=self.image.get_rect()
allsprite=pygame.sprite.Group()
jack=Tom()
allsprite.add(jack)
play=True
clock=pygame.time.Clock()
while play:
    clock.tick(40)
    for event in pygame.event.get():
        if event.type==pygame.QUIT:
            play=False
        c=pygame.image.load("unnamed.jpg").convert_alpha()
        e=pygame.transform.scale(c,(b,a))
        screen.blit(e,(0,0))
        f=pygame.key.get_pressed()
        if f[pygame.K_UP]:
            if jack.rect.y>0:
                jack.rect.y -=10
        if f[pygame.K_DOWN]:
            if jack.rect.y<700:
                jack.rect.y +=10
        if f[pygame.K_LEFT]:
            if jack.rect.x>0:
                jack.rect.x -=10
        if f[pygame.K_RIGHT]:
            if jack.rect.x<900:
                jack.rect.x+=10
        allsprite.draw(screen)
    pygame.display.update()
