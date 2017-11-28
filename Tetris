package com.course.GameTetris;

import java.awt.Color;
import java.awt.Font;
import java.awt.event.KeyEvent;
import java.awt.event.KeyListener;
import java.awt.event.MouseEvent;
import java.awt.event.MouseListener;
import java.util.Random;

@SuppressWarnings("serial")
public class Plansza extends ACanvas implements MouseListener, KeyListener{

    final static short SIZE = 25;
    final static short SZE = SIZE * 10;
    final static short WYS = SIZE * 20;


    final Color[] KOLOR = {Color.GRAY, Color.RED, Color.GREEN, Color.blue, Color.CYAN, Color.MAGENTA, Color.ORANGE, Color.YELLOW, Color.WHITE};

    byte[][] tab = new byte[10][20];
    Random los = new Random();

    Klocek klocek = new Klocek();
    byte klocekX, klocekY;

    boolean kLeft, kRight, kUp, kDown;

    Plansza() {
        super(SZE,WYS);addMouseListener(this);addKeyListener(this);
    }

    @Override
    public void drawImage() {
        key();
        cmpPlansza();
        drukPlansza();
        drukKlocek(klocekX, klocekY);
    }

    private void drukPlansza()
    {
        for (byte x=0; x<10; x++)
            for (byte y=0; y<20; y++)
            {
                grafika.setColor(KOLOR[tab[x][y]]);
                grafika.fillRect(x*SIZE, y*SIZE, SIZE, SIZE);
                grafika.setColor(Color.BLACK);
                if (tab[x][y]>0) grafika.drawRect(x*SIZE, y*SIZE, SIZE-1, SIZE-1);
            }
    }
    private void drukKostka(byte x, byte y, byte k)
    {
        grafika.setColor(KOLOR[k]);
        grafika.fillRect(x*SIZE, y*SIZE, SIZE, SIZE);
        grafika.setColor(Color.BLACK);
        grafika.drawRect(x*SIZE, y*SIZE, SIZE-1, SIZE-1);
    }

    private boolean isLinia(byte y)
    {
        for (byte x=0; x<10; x++) {if (tab[x][y]==0) return false;}
        return true;
    }
    private void setLinia(byte y)
    {
        for (byte x=0; x<10; x++) tab[x][y]=8;
    }
    private void downPlansza(byte y)
    {
        for (byte ty=y; ty>0; ty--)
            for (byte x=0; x<10; x++) tab[x][ty]=tab[x][ty-1];
        for (byte x=0; x<10; x++) tab[x][0]=0;
    }
    private void cmpPlansza()
    {
        for (byte y=0; y<20; y++)
        {
            if (tab[0][y]==8) downPlansza(y);
            if (isLinia(y)) setLinia(y);
        }
    }

    private void drukKlocek(byte x, byte y)
    {
        for (byte tx=0; tx<4; tx++)
            for (byte ty=0; ty<4; ty++)
                if (klocek.tab[tx][ty]) drukKostka((byte)(x+tx), (byte)(y+ty),(byte)(klocek.akKlocek+1));
    }
    @Override
    public void mouseClicked(MouseEvent e) {}

    @Override
    public void mousePressed(MouseEvent e) {}

    @Override
    public void mouseReleased(MouseEvent e) {
        tab[e.getX()/SIZE][e.getY()/SIZE]=1;
    }

    @Override
    public void mouseEntered(MouseEvent e) {}

    @Override
    public void mouseExited(MouseEvent e) {}

    @Override
    public void keyTyped(KeyEvent e) {}

    @Override
    public void keyPressed(KeyEvent e) {
        int k = e.getKeyCode();
        if (k==e.VK_UP) kUp=true;
        if (k==e.VK_DOWN) kDown=true;
        if (k==e.VK_LEFT) kLeft=true;
        if (k==e.VK_RIGHT) kRight=true;
    }

    @Override
    public void keyReleased(KeyEvent e) {
        int k = e.getKeyCode();
        if (k==e.VK_UP) kUp=false;
        if (k==e.VK_DOWN) kDown=false;
        if (k==e.VK_LEFT) kLeft=false;
        if (k==e.VK_RIGHT) kRight=false;}

    private void key()
    {
        if (kUp) klocek.obrut();
        if (kLeft)
        {
            klocekX--;
        }
        if (kRight)
        {
            klocekX++;
        }
    }

}
