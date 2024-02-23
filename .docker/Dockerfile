# fv3-container-test Dockerfile

ARG osversion
ARG imagename
ARG baselibversion
ARG mpiname
ARG mpiversion
ARG compilername
ARG compilerversion

ARG BASE_IMAGE=gmao/${osversion}-${imagename}:${baselibversion}-${mpiname}_${mpiversion}-${compilername}_${compilerversion}
FROM ${BASE_IMAGE}

ARG fv3version

RUN git clone -b ${fv3version} https://github.com/GEOS-ESM/fv3-container-test.git /fv3-container-test-src && \
    cd /fv3-container-test-src && \
    mepo clone && \
    mkdir build && \
    cd build && \
    cmake .. -DCMAKE_INSTALL_PREFIX=/fv3-container-test/install -DBASEDIR=$BASEDIR/Linux -DUSE_F2PY=OFF -DCMAKE_Fortran_COMPILER=$FC -DCMAKE_C_COMPILER=$CC -DCMAKE_CXX_COMPILER=$CXX && \
    make -j $(nproc) install/strip && \
    cd / && \
    rm -rf /fv3-container-test-src
