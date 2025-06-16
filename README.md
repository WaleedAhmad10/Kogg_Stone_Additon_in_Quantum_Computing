OPENQASM 2.0;
include "qelib1.inc";
qreg q[14];
creg c[3];
gate mcx_3 a, b, c, d
{
  h d;
  cu1 ((pi) / 4) c, d;
  cx c, b;
  cu1 (-((pi) / 4)) b, d;
  cx c, b;
  cu1 ((pi) / 4) b, d;
  cx b, a;
  cu1 (-((pi) / 4)) a, d;
  cx c, a;
  cu1 ((pi) / 4) a, d;
  cx b, a;
  cu1 (-((pi) / 4)) a, d;
  cx c, a;
  cu1 ((pi) / 4) a, d;
  h d;
}

x q[1];
x q[2];
x q[3];
cx q[0], q[6];
cx q[2], q[6];
cx q[1], q[7];
cx q[3], q[7];
ccx q[2], q[0], q[4];
ccx q[3], q[1], q[5];
cx q[4], q[9];
ccx q[9], q[7], q[13];
cx q[5], q[10];
cx q[10], q[13];
cx q[13], q[10];
ccx q[5], q[13], q[10];
cx q[6], q[11];
cx q[8], q[11];
cx q[7], q[12];
cx q[9], q[12];
measure q[10] -> c[2];
measure q[11] -> c[0];
measure q[12] -> c[1];
