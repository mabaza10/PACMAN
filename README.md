# PACMAN
PACMAN
import java.util.Scanner;

public class PacMan {
    private static final int SIZE = 5;
    private static final char WALL = '#';
    private static final char PACMAN = 'C';
    private static final char PELLET = '.';
    private static char[][] map = new char[SIZE][SIZE];

    public static void main(String[] args) {
        initMap();
        printMap();

        Scanner scanner = new Scanner(System.in);
        int x = 0;
        int y = 0;

        while (true) {
            System.out.println("Move (WASD): ");
            char move = scanner.nextLine().toUpperCase().charAt(0);

            switch (move) {
                case 'W':
                    y = y > 0 ? y - 1 : y;
                    break;
                case 'A':
                    x = x > 0 ? x - 1 : x;
                    break;
                case 'S':
                    y = y < SIZE - 1 ? y + 1 : y;
                    break;
                case 'D':
                    x = x < SIZE - 1 ? x + 1 : x;
                    break;
                default:
                    System.out.println("Invalid move!");
                    continue;
            }

            if (map[y][x] == PELLET) {
                System.out.println("Yummy!");
            }

            map[y][x] = PACMAN;
            printMap();
        }
    }

    private static void initMap() {
        for (int i = 0; i < SIZE; i++) {
            for (int j = 0; j < SIZE; j++) {
                if (i == 0 || i == SIZE - 1 || j == 0 || j == SIZE - 1) {
                    map[i][j] = WALL;
                } else {
                    map[i][j] = PELLET;
                }
            }
        }
    }

    private static void printMap() {
        for (int i = 0; i < SIZE; i++) {
            for (int j = 0; j < SIZE; j++) {
                System.out.print(map[i][j]);
            }
            System.out.println();
        }
    }
}
