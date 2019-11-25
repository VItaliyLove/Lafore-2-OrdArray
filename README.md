# Lafore-2-OrdArray

class Algorithm {

    static class OrdArray {
        private long[] a;
        private int nElems;

        public OrdArray(int size){
            a = new long[size];
            nElems = 0;
        }

        public int getSize(){
            return nElems;
        }

        public void display(){
            for (int j = 0; j < nElems; j++)
                System.out.print(a[j] + " ");
            System.out.println();
        }

        public void insert(long elem){
            int j;
            for (j = 0; j < nElems; j++)
                if (a[j] > elem)
                    break;
            for (int k = nElems; k > j; k--)
                a[k] = a[k-1];
            a[j] = elem;
            nElems++;
        }

        public boolean delete(long elem){
            int j;
            for (j = 0; j < nElems; j++)
                if (a[j] == elem)
                    break;
            if (j == nElems)
                return false;
            else {
                for (; j < nElems - 1; j++)
                    a[j] = a[j + 1];
                nElems--;
                return true;
            }
        }

        public int find(long searchKey) {
            int lowerBound = 0;
            int highBound = nElems-1;
            int curPos = (lowerBound+highBound)/2;

            while (true) {
                if (a[curPos] == searchKey)
                    return curPos;
                else if (lowerBound > highBound)
                    return -1;
                else
                    if (a[curPos] > searchKey)
                        highBound = curPos-1;
                    else
                        lowerBound = curPos+1;
            }
        }
    }

    public static void main(String[] arg) {
        OrdArray ordArray = new OrdArray(5);

        ordArray.insert(7);
        ordArray.insert(5);
        ordArray.insert(3);
        ordArray.insert(1);
        ordArray.display();
        System.out.println(ordArray.getSize());
        System.out.println(ordArray.find(3));
        ordArray.delete(5);
        ordArray.display();
        System.out.println(ordArray.getSize());
    }
}
