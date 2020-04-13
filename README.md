# KnightPath
# Program to visualize the path of a knight over a board
from cs1lib import start_graphics, clear, draw_circle, draw_rectangle, set_fill_color, set_stroke_color
# parameters
n=50
center_x=0
center_y=0
scale=4
def makesquare(a,b):
    draw_rectangle(a,b,scale,scale)
board = [[-1]*(2*n+1) for _ in range(2*n+1)]

#initial value
board[n][n]=0
# algorithm to make grid of numbers
def makegrid():
    r=0
    while (r<2*n+1):
        c=0
        while (c<2*n+1):
            if (board[r][c]>=0):
                if (r<=2*n-1 and c<=2*n-2):
                    if (board[r+1][c+2]<0 or board[r+1][c+2]>board[r][c]):
                        board[r+1][c+2]=board[r][c]+1
                if (r<=2*n-1 and c>=2):
                    if (board[r+1][c-2]<0 or board[r+1][c-2]>board[r][c]):
                        board[r+1][c-2]=board[r][c]+1
                if (r>=1 and c<=2*n-2):
                    if (board[r-1][c+2]<0 or board[r-1][c+2]>board[r][c]):
                        board[r-1][c+2]=board[r][c]+1
                if (r>=1 and c>=2):
                    if (board[r-1][c-2]<0 or board[r-1][c-2]>board[r][c]):
                        board[r-1][c-2]=board[r][c]+1
                if (r<=2*n-2 and c<=2*n-1):
                    if (board[r+2][c+1]<0 or board[r+2][c+1]>board[r][c]):
                        board[r+2][c+1]=board[r][c]+1
                if (r<=2*n-2 and c>=1):
                    if (board[r+2][c-1]<0 or board[r+2][c-1]>board[r][c]):
                        board[r+2][c-1]=board[r][c]+1
                if (r>=2 and c<=2*n-1):
                    if (board[r-2][c+1]<0 or board[r-2][c+1]>board[r][c]):
                        board[r-2][c+1]=board[r][c]+1
                if (r>=2 and c>=1):
                    if (board[r-2][c-1]<0 or board[r-2][c-1]>board[r][c]):
                        board[r-2][c-1]=board[r][c]+1
            c+=1
        r+=1
# check if filled in
def repeat():
    r=0
    while (r<2*n+1):
        c=0
        while (c<2*n+1):
            if (board[r][c]<0):
                return True
            c+=1
        r+=1
    return False

# run grid until grid filled in
while (repeat()):
    makegrid()


def draw():
    clear()
    m=0
    while (m<2*n+1):
        p=0
        while (p<2*n+1):
            set_fill_color((board[m][p])*(3.0)/(2*n+4),0,0)
            set_stroke_color((board[m][p])*(3.0)/(2*n+4),0,0)
            makesquare(center_x+scale*m,center_y+scale*p)
            
            p+=1
        m+=1
print("hello")
start_graphics(draw)
