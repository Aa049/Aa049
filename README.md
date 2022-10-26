public class VaccineDose
{
    public static final int JANSSEN = 1, ASTRAZENECA = 2, PFIZER = 3;
    private int         type;
    private double      dose;
    private TimeInstant prepTime;
    private String      sip;
    public VaccineDose(int t, double d, int h, int m, String s)
    {
        type = t;
        dose = d;
        prepTime = new TimeInstant(h, m);
        sip = s;
}
    public VaccineDose()
    {
type = ASTRAZENECA;
dose = 0.5;
prepTime = new TimeInstant();
sip = "";
// alternatively:
// this(ASTRAZENECA, 0.5, 0, 0, ""); // prepTime = new TimeInstant();
}
    public boolean equals(Object o)
    {
        if (o instanceof VaccineDose) {
            VaccineDose other = (VaccineDose)o;
return this.type == other.type
&& Math.abs(this.dose - other.dose) < 1.0e-3 && this.prepTime.equals(other.prepTime);
        } else {
            return false;
} }
    public int compareTo(VaccineDose other)
    {
int diff = type - other.type; if (diff == 0) {
if (dose < other.dose) { diff = -1;
} else if (dose > other.dose) { diff = 1;
}
// alternatively:
//diff = (int) Math.signum(dose - other.dose);
}
        return diff;
    }
    public String toString() {
        String res = "Vaccine: ";
        switch (type) {
} }
