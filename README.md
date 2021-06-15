	
	import java.io.BufferedReader;
	import java.io.IOException;
	import java.io.InputStreamReader;
	import java.util.StringTokenizer;
	
	public class Main {
		public static int Min = Integer.MAX_VALUE;
		public static int Max = Integer.MIN_VALUE;
		public static int Number[];
		public static int operator[] = new int[4];
		public static int N;
	
		public static void main(String[] args) throws IOException {
			BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
			N = Integer.parseInt(br.readLine());
			StringTokenizer st = new StringTokenizer(br.readLine(), " ");
			Number = new int[st.countTokens()];
			for (int i = 0; i < Number.length; i++) {
				Number[i] = Integer.parseInt(st.nextToken());
			}
			
			st = new StringTokenizer(br.readLine(), " ");
			for (int i = 0; i < 4; i++) {
				operator[i] = Integer.parseInt(st.nextToken());
			}
			numberCompare(Number[0], 1);
			System.out.println(Max);
			System.out.println(Min);
		}
	
		public static void numberCompare(int number, int idx) {
			if (N == idx) {
				Max = Math.max(Max, number);
				Min = Math.min(Min, number);
				return;
			}
			for (int i = 0; i < 4; i++) {
				if (operator[i] > 0) {
					operator[i]--;
					switch (i) {
					case 0:
						numberCompare(number + Number[idx], idx + 1);
						break;
					case 1:
						numberCompare(number - Number[idx], idx + 1);
						break;
					case 2:
						numberCompare(number * Number[idx], idx + 1);
						break;
					case 3:
						numberCompare(number / Number[idx], idx + 1);
						break;
					}
					operator[i]++;
				}
			}
		}
	}
