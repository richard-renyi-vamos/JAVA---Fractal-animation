CHATGPT CONVERSATION

  *****************************

create a FRACTAL ANIMATION in JAVA
ChatGPT said:
Here's a simple fractal animation in Java using the Swing library and recursion to generate a fractal tree. The animation grows dynamically, creating a mesmerizing effect. You can modify the parameters to generate different fractal styles.

Fractal Animation

Answer in chat instead
This Java program creates a fractal tree animation that evolves over time using recursion and a timer. 🌿✨ You can tweak the angle, depth, or colors for different fractal effects! Let me know if you need modifications! 🚀🔥

********************************

  import javax.swing.*;
import java.awt.*;

public class FractalTreeAnimation extends JPanel {
    private int depth = 0; // Initial recursion depth
    
    public FractalTreeAnimation() {
        Timer timer = new Timer(500, e -> {
            depth++;
            repaint();
        });
        timer.start();
    }
    
    @Override
    protected void paintComponent(Graphics g) {
        super.paintComponent(g);
        Graphics2D g2d = (Graphics2D) g;
        g2d.setRenderingHint(RenderingHints.KEY_ANTIALIASING, RenderingHints.VALUE_ANTIALIAS_ON);
        
        int startX = getWidth() / 2;
        int startY = getHeight() - 100;
        int length = 100;
        
        drawFractal(g2d, startX, startY, -90, length, depth);
    }
    
    private void drawFractal(Graphics2D g, int x1, int y1, double angle, int length, int depth) {
        if (depth == 0) return;
        
        int x2 = x1 + (int) (Math.cos(Math.toRadians(angle)) * length);
        int y2 = y1 + (int) (Math.sin(Math.toRadians(angle)) * length);
        
        g.setColor(Color.getHSBColor(depth * 0.1f, 1f, 1f)); // Dynamic color change
        g.drawLine(x1, y1, x2, y2);
        
        drawFractal(g, x2, y2, angle - 30, length - 10, depth - 1);
        drawFractal(g, x2, y2, angle + 30, length - 10, depth - 1);
    }
    
    public static void main(String[] args) {
        JFrame frame = new JFrame("Fractal Tree Animation");
        FractalTreeAnimation panel = new FractalTreeAnimation();
        frame.add(panel);
        frame.setSize(800, 600);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setVisible(true);
    }
}
