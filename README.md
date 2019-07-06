# Rangkuman_Modul2

Stacks adalah satu struktur data dimana penambahan dan penghapusan data, hanya dapat dilakukan pada satu ujung yang sama,
atau yang biasa dikenal dengan istilah top. karena samakin jauh posisi data dari top maka data tersebut diindikasikan
berada di stack lebih lama dibandingkan dengan data yang berada dekat pada data di posisi top.

Terdapat operasi dasar pada Stacks,
- stack () adalah inisialisasi stack yang kosong
- push(data) adalah penambahan data baru pada posisi top dari stack
- pop()adalah penghapusan data yang terdapat di posisi top dari stack.

Sedangkan return value dari fungsi ini adalah data yang dihapus dari stack tersebut
- peek() adalah informasi data yang terletak pada posisi top
- isEmpty() adalah untuk memeriksa apakah stack dalam keadaan kosong
- size() adalah informasi jumlah data yang terdapat pada stack

      def stack():
          s=[]
          return (s)
      def push(s,data):
          s.append(data)
      def pop(s):
          data=s.pop()
          return(data)
      def peek(s):
          return(s[len(s)-1])
      def isEmpty(s):
          return (s==[])
      def size(s):
          return(len(s))
          
contoh penggunaan fungsi-fungsi stacks yang telah dibuat:
    st=stack()
    isEmpty(st)
True

    push(st,100)
    push(st,23)
    push(st,34)
    pop(st)
    push(st,56)
    pop(st)
    print(st)
[100, 23]


 implementasi untuk penggunaan stacks ada 2, yaitu delimiter matching dan konversi desimal ke biner
 1.delimiter matching
   Parentheses sering digunakan untuk urutan penyelesaian dalam persamaan Matematika, seperti contoh berikut:
   P = 5 x (4 + 5) / ((3 + 2) x (10 - 8))
   secara umum  pemeriksaan parentheses ada 2, yaitu '{ }', '', dan '( )'
   
   sedangkan tahapan / algoritmanya bisa dilihat dibawah ini:
    a. Baca setiap karakter yang terdapat pada suatu string matematika
    b. Jika karakter adalah kurung buka, maka masukkan dalam stack
    c. Jika karakter adalah kurung tutup, ada beberapa kondisi yang harus diperiksa, yaitu :
    d. Jika stack dalam keadaan empty, maka jumlah kurung tutup lebih banyak daripada kurung buku
    e. Jika stack dalam keadaan tidak empty, maka maka pop stack, dan cocokkan karakter hasil pop dengan kurung tutup, jika sejenis,
       maka matched, jika tidak maka jenis kurung tidak sama
    f. Jika semua karakter telah terbaca, dan stack masih dalam keadaan terisi (tidak empty), maka jumlah kurung buka lebih banyak
       daripada kurung tutup
       
fungsi untuk pengecekan kurung pada suatu string matematika
      def stack():
          s=[]
          return (s)
      def push(s,data):
          s.append(data)
      def pop(s):
          data=s.pop()
          return(data)
      def peek(s):
          return(s[len(s)-1])
      def isEmpty(s):
          return (s==[])
      def size(s):
          return(len(s))
          
      def paranthesesCheck(strMath):
          operandStack=stack()
          lenMath=len(strMath)
          openOperand='({['
          closeOperand=')}]'
          #print(lenMath)
          i=0
          Matched=True;
          while i<(lenMath):
              #print(i,'=',strMath[i])
              if strMath[i] in openOperand:
                  push(operandStack,strMath[i])
                  #print(operandStack)
              elif strMath[i] in closeOperand:
                  if not (isEmpty(operandStack)):
                      top=pop(operandStack)
                      #print("top=",top)
                      #print (operandStack)
                      if openOperand.index(top)==closeOperand.index(strMath[i]):
                          Matched=Matched and True
                      else:
                          Matched=Matched and False
                          print ('Kurung Buka dan Kurang Tutup tidak Cocok')
                  else:
                      Matched=Matched and False
                      print('Jumlah Kurung Tutup lebih banyak')
              i=i+1
              #print(Matched)
          if not(isEmpty(operandStack)):
              Matched=False
              print('Jumlah Kurung Buka Lebih banyak')
          return(Matched)
